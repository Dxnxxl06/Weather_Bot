# Weather Bot - Clima Automatizado

## Descripción

Este proyecto es un bot de clima automatizado construido con n8n. Envía actualizaciones del clima de varias ciudades colombianas (Bucaramanga, Bogotá, Medellín y Cali) a través de un bot de Telegram cada hora. Utiliza la API de Open-Meteo para obtener datos meteorológicos y OpenAI para generar mensajes amigables.

## Funcionalidades

- **Actualización automática**: Se ejecuta cada hora mediante un trigger programado.
- **Ciudades soportadas**: Bucaramanga, Bogotá, Medellín y Cali.
- **Mensaje personalizado**: Usa IA para generar mensajes cortos y amigables.
- **Envío por Telegram**: Notificaciones directas al chat configurado.

## Requisitos

- **n8n**: Plataforma de automatización de workflows.
- **API de OpenAI**: Para generar mensajes con IA.
- **Bot de Telegram**: Configurado con token de API.

## Instalación

1. Instala n8n si no lo tienes: `npm install -g n8n`
2. Ejecuta n8n: `n8n`
3. Importa el archivo `Clima Automatizado.json` en tu instancia de n8n.
4. Configura las credenciales necesarias (ver sección de Configuración).

## Configuración

### Credenciales de OpenAI
- Crea una cuenta en OpenAI y obtén tu API key.
- En n8n, configura la credencial "Cuenta Nueva" con tu API key.

### Credenciales de Telegram
- Crea un bot en Telegram usando @BotFather y obtén el token.
- Configura la credencial "Telegram account" con el token.
- Obtén el Chat ID del chat donde quieres recibir los mensajes (por ejemplo, tu propio chat).

### Ajustes del Workflow
- En el nodo "Envia mensaje bot telegram", actualiza el `chatId` con tu Chat ID.
- El workflow está configurado para Bucaramanga por defecto; puedes modificar las coordenadas en el nodo "Dar data clima" para otras ciudades.

## Uso

1. Activa el workflow en n8n.
2. El trigger se ejecutará automáticamente cada hora.
3. Recibirás mensajes de clima en tu bot de Telegram.

## Estructura del Workflow

1. **Trigger ejecuta 1h**: Inicia el workflow cada hora.
2. **Dar data clima**: Proporciona datos de ciudades con coordenadas.
3. **HTTP Request**: Consulta la API de Open-Meteo para obtener el clima actual.
4. **Code in JavaScript1**: Procesa los datos del clima y crea un mensaje base.
5. **Se crea mendaje texto con IA**: Usa OpenAI para generar un mensaje amigable.
6. **Envia mensaje bot telegram**: Envía el mensaje final por Telegram.

## Licencia

Este proyecto está bajo la licencia MIT.