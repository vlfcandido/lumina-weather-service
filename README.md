
# lumina-weather-service

Microserviço desenvolvido em TypeScript com Node.js para fornecer a previsão do tempo do evento Lumina Fest. Ele expõe uma rota HTTP `/forecast` integrada à WeatherAPI e retorna a previsão dos próximos três dias em formato estruturado, pensado para consumo por um chatbot na plataforma Blip.

## Tecnologias utilizadas

- TypeScript
- Node.js
- Express
- Axios
- Dotenv
- ngrok (para expor localmente via HTTPS)
- WeatherAPI (integração externa)
- Blip (canal de atendimento com chatbot)

## Instalação

```bash
git clone https://github.com/seu-usuario/lumina-weather-service.git
cd lumina-weather-service
npm install
```

## Configuração

Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:

```env
WEATHER_API_KEY=4d104eef44fe43b08ba215912250904
PORT=3000
```

A chave acima está funcional para testes com o plano gratuito da WeatherAPI: https://www.weatherapi.com/

## Executando localmente

```bash
npx ts-node src/index.ts
```

Para facilitar a integração externa (como com o Blip), utilize o ngrok:

```bash
ngrok http 3000
```

Utilize a URL gerada pelo ngrok no Blip para realizar a requisição HTTP GET no endpoint `/forecast`.

## Exemplo de resposta

```json
{
  "cidade": "Aurora",
  "dias": [
    {
      "data": "2025-04-18",
      "condicao": "Ensolarado",
      "temperaturaMax": "27°C",
      "temperaturaMin": "18°C",
      "chanceDeChuva": "5%"
    },
    {
      "data": "2025-04-19",
      "condicao": "Parcialmente nublado",
      "temperaturaMax": "25°C",
      "temperaturaMin": "19°C",
      "chanceDeChuva": "20%"
    },
    {
      "data": "2025-04-20",
      "condicao": "Chuva leve",
      "temperaturaMax": "23°C",
      "temperaturaMin": "20°C",
      "chanceDeChuva": "60%"
    }
  ]
}
```

## Estrutura do projeto

- `src/index.ts`: entrada principal da aplicação
- `buildWeatherUrl`: função pura para montar a URL da API externa
- `formatWeatherResponse`: função pura para estruturar a resposta em um formato amigável
- `/forecast`: rota principal que retorna os dados formatados

## Boas práticas adotadas

- Uso de funções puras e imutabilidade
- Separação clara de responsabilidades
- Tipagem explícita com TypeScript
- Comentários explicativos e semânticos
- Código preparado para testes e manutenção

## Observações

- O foco deste projeto foi a resolução técnica e direta do problema central proposto: integração entre Blip e previsão climática.
- Não foram implementados:
  - Bot de exceptions para erros genéricos
  - Relatórios e métricas personalizadas (trackings no Blip)


## Objetivo do projeto

Esse microserviço foi desenvolvido como parte de um desafio técnico focado em boas práticas de backend, integração com APIs externas e construção de soluções com propósito real e foco em usabilidade.
