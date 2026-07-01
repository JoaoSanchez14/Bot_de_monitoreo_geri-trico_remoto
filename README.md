# Bot de monitoreo geriátrico remoto
Bot de Telegram pensado para que un cuidador (familiar o técnico de enfermería) lleve un diario clínico de un adulto mayor con hipertensión y/o diabetes, y pueda compartirlo con el médico tratante.

## Funcionalidades
- Registro de presión arterial y glucosa en sangre, varias veces al día.
- Confirmación de toma de medicamentos.
- Registro de síntomas con nivel de intensidad.
- Cálculo automático de promedios del período.
- Motor de reglas que evalúa el riesgo y detecta valores peligrosos reiterados.
- Generación de gráficos temporales de presión y glucosa.
- Generación de un informe clínico narrativo.
- Persistencia de datos entre sesiones (vía `pickle`).

## Requisitos
- Python 3.9+
- Un bot de Telegram creado con [@BotFather](https://t.me/BotFather) y su token.

### Dependencias
```bash
pip install python-telegram-bot nest_asyncio matplotlib numpy pytz
```

## Configuración
El bot necesita la variable de entorno `TELEGRAM_TOKEN` con el token de tu bot de Telegram.

En Google Colab:
Guardá el token como secreto en Colab con el nombre `TELEGRAM_TOKEN` (menú de "Secrets" 🔑).

En local:
```bash
export TELEGRAM_TOKEN="tu_token_aquí"
```

⚠️ Nunca subas tu token al repositorio. El notebook ya está preparado para leerlo desde `google.colab.userdata` o desde la variable de entorno, nunca hardcodeado.

## Uso
1. Abrí el notebook `Bot_de_monitoreo_geriátrico_remoto.ipynb` en Google Colab (o Jupyter local).
2. Configurá el token como se indica arriba.
3. Ejecutá todas las celdas en orden.
4. La última celda (`Iniciar()`) levanta el bot con polling.

## Almacenamiento de datos
Los datos de pacientes se guardan localmente en `./datos_bot/usuarios/` y en `datos_pacientes.pkl` (persistencia de `python-telegram-bot`). Estos archivos no se suben al repositorio (ver `.gitignore`) porque contienen información clínica sensible.

## ⚠️ Aviso importante
Este proyecto es un prototipo educativo/demo. Maneja datos de salud (presión arterial, glucosa, síntomas, medicación) que son datos sensibles. No está pensado para uso en producción con pacientes reales sin antes incorporar:

- Cifrado de datos en reposo y en tránsito.
- Consentimiento informado del usuario/paciente.
- Cumplimiento de normativa de protección de datos de salud aplicable en tu país (p. ej. Ley de Protección de Datos Personales en Perú, HIPAA en EE.UU., etc.).
- Control de acceso y autenticación robusta.
