# ChatBot con Python y Telegram
En esta actividad analizaremos el uso de expresiones regulares con Python para la comunicacion entre el usuario y un bot generado en telegram, 
para los cuales se mostrara el codigo y las correspondientes pruebas de su funcionamiento

## Codigo del funcionamiento del Bot mediante Regex

```python
import logging
import re
import datetime

from telegram import ForceReply, Update
from telegram.ext import Application, CommandHandler, ContextTypes, MessageHandler, filters

# Enable logging
logging.basicConfig(format="%(asctime)s - %(name)s - %(levelname)s - %(message)s", level=logging.INFO)
logging.getLogger("httpx").setLevel(logging.WARNING)
logger = logging.getLogger(_name_)

# Expresiones regulares
expresion_saludo = re.compile(r"hello|hi|hey|hola", re.IGNORECASE)
expresion_estado = re.compile(r"(?:¿)?c[oó]mo est[aá]s\??", re.IGNORECASE)
expresion_bien = re.compile(r"estoy bien", re.IGNORECASE)
expresion_mal = re.compile(r"estoy mal", re.IGNORECASE)
expresion_hora = re.compile(r"dame la hora", re.IGNORECASE)
expresion_operacion = re.compile(r"cu[aá]nto es (\d+)\s*\\s(\d+)", re.IGNORECASE)
expresion_animal = re.compile(r"Cual es el animal mas fiel", re.IGNORECASE)
expresion_jugador = re.compile(r"Cual es el mejor jugador brasileño", re.IGNORECASE)

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Send a message when the command /start is issued."""
    user = update.effective_user
    await update.message.reply_html(
        rf"Hi {user.mention_html()}!",
        reply_markup=ForceReply(selective=True),
    )


async def help_command(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Send a message when the command /help is issued."""
    await update.message.reply_text("Help!")


async def echo(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Echo the user message if it matches any regular expression."""
    message_text = update.message.text
    if expresion_saludo.search(message_text):
        await update.message.reply_text("¡Hola! ¿Cómo estás?")
    elif expresion_estado.search(message_text):
        await update.message.reply_text("Estoy bien, no hay motivo de inconformidad.")
    elif expresion_hora.search(message_text):
        now = datetime.datetime.now()
        await update.message.reply_text(f"La hora actual es: {now.strftime('%H:%M:%S')}")
    elif expresion_operacion.search(message_text):
        match = expresion_operacion.search(message_text)
        resultado = int(match.group(1)) + int(match.group(2))
        await update.message.reply_text(f"El resultado de la multiplicacion es: {resultado}")
    elif expresion_animal.search(message_text):
        await update.message.reply_text("El perro es el animal mas leal.")
    elif expresion_jugador.search(message_text):
        await update.message.reply_text("Neymar JR, Obviamente.")    
    elif expresion_bien.search(message_text):
        await update.message.reply_text("Me alegro.")
    elif expresion_mal.search(message_text):
        await update.message.reply_text("Lo siento, espero que te sientas mejor pronto.")
    else:
        await update.message.reply_text("No entendí tu mensaje.")


def main() -> None:
    """Start the bot."""
    application = Application.builder().token("6428451034:AAHeEEZSxH2UyqH026KgricUGvyKODSx2CQ").build()

    application.add_handler(CommandHandler("start", start))
    application.add_handler(CommandHandler("help", help_command))
    application.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, echo))

    application.run_polling(allowed_updates=Update.ALL_TYPES)


if _name_ == "_main_":
    main()
```

# Captura del correcto funcionamiento del bot

![Imagen de WhatsApp 2024-04-17 a las 20 30 41_8eafcc97](https://github.com/DonovanFranco/Lenguajes_Automatas_1/assets/161343179/fcfbbaa1-1f46-4a45-b902-08fbcbf9b050)


