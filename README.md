# Fênix Data Solution

## Painel para análise conjunta de respostas de PSAV

![Fênix Data Solution](public/og.png)

O **Fênix Data Solution** é um painel investigativo para leitura, organização e correlação de respostas fornecidas por Prestadores de Serviços de Ativos Virtuais (PSAV). A aplicação transforma arquivos técnicos de diferentes empresas em uma visão comum do caso, preservando a origem das informações e permitindo análises individuais ou conjuntas.

O projeto foi desenvolvido para apoiar a revisão de movimentações financeiras, contrapartes, endereços blockchain, acessos, dispositivos, dados cadastrais e possíveis relações entre contas ou operações. As correlações apresentadas são indícios para análise e não constituem, isoladamente, prova de identidade, titularidade ou participação comum.

## Fontes atualmente suportadas

| Empresa ou serviço | Formato aceito | Cobertura principal |
|---|---|---|
| Binance | `.xlsx` | Cadastro e KYC, saldos, cripto, fiat, P2P, Pay, Send, negociações, extratos internos, acessos e dispositivos, conforme as abas fornecidas |
| Gate.io | `.zip` | Dados cadastrais, movimentações, saldos, acessos e demais informações presentes no pacote suportado |
| OKX | `.xlsx` | Cadastro, depósitos, saques, saldos e informações técnicas disponíveis |
| Bybit | `.xlsx` | Cadastro, depósitos, saques, saldos e informações técnicas disponíveis |
| Bitget | `.xlsx` | Cadastro, depósitos, saques, saldos e informações técnicas disponíveis |
| ChangeNOW | `.csv` | Tickets de swap, pontas de entrada e saída, endereços, TXIDs e contexto técnico da solicitação |

O painel pode detectar automaticamente a origem do arquivo ou permitir a seleção manual da empresa.

## Principais funções

### Resumo do caso

- Indicadores de entradas, saídas, movimentações e cobertura das fontes.
- Saldo total estimado e composição das posições quando informados pelo PSAV.
- Visão executiva dos principais pontos que merecem revisão.
- Separação entre dados encontrados, não fornecidos, não aplicáveis e parcialmente interpretados.

### Movimentações financeiras

- Lista unificada de operações cripto e fiat.
- Categorias específicas para P2P, Binance Pay, Binance Send, negociações, OTC e extratos internos, quando disponíveis.
- Filtros por conta, empresa, período, ativo, rede, direção, status, endereço, TXID e texto livre.
- Exibição do valor original, equivalente monetário, contraparte ou canal, situação e referência de origem.
- Distinção entre operações concluídas, tentativas, falhas, cancelamentos, estornos, pendências e estados desconhecidos, conforme os dados da fonte.

### Análise conjunta entre contas e empresas

- Comparação de dois ou mais arquivos no mesmo caso, inclusive de empresas diferentes.
- Cruzamento de endereços, TXIDs, IPs, dispositivos, contrapartes, dados KYC, dados fiat e outros identificadores compatíveis.
- Detecção de transferências rastreáveis entre contas por TXID ou por critérios compatíveis de ativo, rede, valor e tempo.
- Matriz de relações, grafo de indicadores compartilhados, linha do tempo e visualização de fluxo.
- Classificação das relações por força e acesso às evidências que sustentam cada resultado.

### Percurso do dinheiro

- Percurso documentado dos eventos em ordem cronológica.
- Reconstrução de percursos prováveis a partir das operações disponíveis.
- Separação entre vínculo documentado, operação compatível e possibilidade investigativa.
- Suporte a trajetos que passam por contas ou empresas distintas.
- Indicação explícita de lacunas, alternativas concorrentes e limites da reconstrução.

### Contrapartes e endereços

- Ranking de origens de depósitos e destinos de saques.
- Consolidação de contrapartes e identificadores informados nas operações.
- Atribuição manual de endereços a investigados, exchanges, serviços de swap, mixers, entidades sancionadas ou outros serviços.
- Exclusão justificada de carteiras custodiais das correlações, sem remover os registros originais.
- Tratamento específico de endereços de serviço da ChangeNOW para evitar vínculos indevidos entre usuários.

### Acessos e dispositivos

- Resumo de IPs, localizações informadas, provedores, dispositivos e eventos de acesso.
- Registros detalhados de dispositivos e acessos recentes, quando fornecidos.
- Correlação temporal entre eventos técnicos e movimentações.
- Consulta opcional do provedor de um IP selecionado.

### Titular, KYC e instrumentos de pagamento

- Exibição controlada dos dados cadastrais do titular.
- Leitura de documentos e imagens incorporadas ao relatório, quando disponíveis.
- Organização de contas bancárias, chaves, meios de pagamento e demais instrumentos declarados pela fonte.
- Proteção visual dos campos sensíveis até que o analista escolha exibi-los.

### Valoração histórica em reais

- Alternância global entre USD e BRL.
- Conversão pela cotação histórica do dólar de venda do Banco Central quando a fonte informa equivalente em USD.
- Consulta do preço histórico do ativo diretamente em BRL pela CoinGecko quando não existe equivalente em USD.
- Uso de dados públicos da Binance como alternativa, com conversão pelo câmbio do Banco Central.
- Memória de cálculo por operação, incluindo critério, data da cotação, fórmula e fonte utilizada.
- Importação opcional de CSV de preços para complementar ou substituir cotações automáticas.

### Gestão do caso

- Persistência automática do caso no navegador por meio de IndexedDB.
- Importação de vários arquivos sem necessidade de recarregar os anteriores.
- Exportação e importação do caso em JSON para transferência entre dispositivos.
- Nome do caso, seleção de contas e preferências mantidos localmente.
- Notas, etiquetas e descarte justificado de falsos positivos.
- Caderno do caso com vínculo ao registro ou indicador analisado.
- Seletor de fuso horário para exibição em UTC ou `America/Sao_Paulo`.
- Encerramento do caso com limpeza dos dados armazenados no dispositivo.

### Procedência e integridade

- Hash SHA-256 do arquivo importado.
- Identificação da versão do importador utilizada.
- Preservação de arquivo, aba, linha e campos de origem sempre que disponíveis.
- Acesso contextual às evidências usadas nos resumos, relações e correlações.
- Avisos de qualidade para valores, datas ou estruturas ambíguas.

### Usabilidade

- Interface em português, inglês e espanhol.
- Layout responsivo para desktop e telas menores.
- Prévia anonimizada para conhecer o painel sem importar dados reais.
- Versão web e geração de um arquivo HTML único para uso offline.

## Privacidade

O processamento dos arquivos ocorre no próprio navegador. Os relatórios importados, documentos de KYC, anotações e dados do caso não são enviados pelo painel a um servidor de análise.

Existem apenas consultas externas específicas e transparentes:

- para valoração em reais, são enviados o símbolo do ativo e o intervalo de datas às fontes públicas de cotação;
- na consulta opcional de provedor de IP, somente o IP selecionado é enviado ao serviço externo indicado na interface.

Antes de publicar exemplos, capturas de tela ou arquivos de teste, remova dados pessoais, documentos, endereços, TXIDs e demais informações sensíveis.

## Critérios de interpretação

O Fênix Data Solution segue alguns princípios para reduzir conclusões indevidas:

- coincidência não significa identidade;
- endereço blockchain não identifica automaticamente uma pessoa;
- IP compartilhado ou dispositivo semelhante não comprova controle comum;
- transferência interna não deve ser contada como nova entrada ou saída externa;
- tentativa de saque não equivale a saque concluído;
- proximidade de valor e horário pode sugerir uma relação, mas não documenta por si só o percurso do dinheiro;
- campos ausentes não são convertidos silenciosamente em valor zero;
- o dado original e sua referência devem prevalecer sobre qualquer interpretação derivada.

## Como executar o projeto

### Requisitos

- Node.js `22.13.0` ou superior
- npm

### Instalação

```bash
npm install
```

### Ambiente de desenvolvimento

```bash
npm run dev
```

### Build da aplicação web

```bash
npm run build
```

### Gerar a versão offline

```bash
npm run build:offline
```

O arquivo HTML único é gerado em `offline-dist/offline/index.html`.

## Testes

Os testes atuais cobrem importação e regressão das fontes, ChangeNOW, ampliação Binance, percurso provável e transferência de casos.

```bash
npm run test:changenow
npm run test:binance-expanded
npm run test:exchange-regression
npm run test:probable-flow
npm run test:case-transfer
```

## Tecnologias principais

- React 19 e TypeScript
- vinext e Vite
- Tailwind CSS
- shadcn/ui e Base UI
- ExcelJS para leitura de planilhas
- Recharts para visualizações
- IndexedDB para persistência local
- Cloudflare Workers para a versão web

## Estrutura resumida

```text
app/          páginas, layout e estilos globais
components/   interface, tabelas, filtros e visualizações
lib/          importadores, modelo do caso, correlações e valoração
offline/      entrada da versão HTML offline
public/       identidade visual e imagens públicas
tests/        testes de importação, regressão e regras investigativas
```

## Aviso

Esta ferramenta auxilia a organização e a análise técnica de dados fornecidos por PSAV. Ela não substitui validação humana, documentação complementar, perícia especializada ou os procedimentos jurídicos aplicáveis ao caso.

---

**Fênix Data Solution** — desenvolvido por Vytautas Zumas.
