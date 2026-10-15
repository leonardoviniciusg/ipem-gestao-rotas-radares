# 📍 Agendamento e Roteirização Inteligente de Radares (Power Apps)

Solução corporativa desenvolvida em **Microsoft Power Apps (Canvas / Power Fx)** focada na otimização logística de rotas e agendamento de verificações metrológicas de instrumentos (radares de trânsito).

---

## 🎯 Problema de Negócio
O planejamento de vistorias técnicas de radares rodoviários e urbanos exige equilibrar restrições operacionais severas:
* Capacidade operacional diária (meta de faixas/dia).
* Janela horária estrita (08h30 às 16h00 sem pernoite ou até 17h00 com pernoite).
* Cidades autorizadas para diárias e proibição de deslocamentos com rotas dispersas.
* Agrupamento geográfico sequencial por empresa operadora e rodovia, evitando trânsito em zigue-zague.

---

## 💡 A Solução
O aplicativo foi arquitetado em 3 etapas integradas:

1. **Gestão de Pendentes & Prompt Generator para IA:**
   * Filtragem multidimensional e busca textual de ordens de serviço (OS).
   * Geração automatizada de prompt estruturado contendo as restrições logísticas.
   * Integração com modelos LLM via entrada JSON com validação instantânea (`ParseJSON`) e criação automática de rotas.

2. **Edição e Lançamento de Rotas:**
   * Gerenciamento de rotas ativas (adicionar/remover OS, ajuste fino sequencial com subida/descida de ordem).
   * Parametrização horária de agendamento por parada.
   * Integração direta com Google Maps gerando URLs dinâmicas com múltiplos waypoints.
   * Lançamento em lote com validações de consistência.

3. **Distribuição por Equipes & Calendário Operacional:**
   * Balanceamento dinâmico de carga de trabalho entre Equipes (KPI de faixas em tempo real).
   * Alocação sequencial de dias de rota (`dia_ref`) com reordenação facilitada.
   * Seletor de datas e persistência atômica no banco de dados (`Patch` em lote via `ForAll`).

---

## 🛠️ Tecnologias & Arquitetura

* **Front-end / Engine:** Power Apps Canvas (Modern Fluent UI Controls, Auto-Layout Containers).
* **Linguagem:** Power Fx estruturado com funções avançadas (`With`, `ForAll`, `Patch`, `ParseJSON`, `Sequence`, `SortByColumns`).
* **Design & UX:** Interface responsiva em Grid 48 colunas x 19 linhas, HTML Viewer para cartões de métricas avançadas (CSS inline).
* **Nomenclatura:** Padrão estrito de prefixos PascalCase (`con_`, `gal_`, `btn_`, `lbl_`, `txt_`, `dtp_`, `rec_`).

---

## 🖥️ Telas do Sistema

### 1. Ordens Pendentes & Painel de IA
> *[Insira aqui uma captura de tela ou GIF mostrando a seleção de OS e o JSON da IA sendo aplicado]*

### 2. Edição de Rotas & Mapa Dinâmico
> *[Insira aqui a captura de tela da galeria de rotas e o botão do Google Maps]*

### 3. Agendamento e Balanceamento de Equipes
> *[Insira aqui a captura mostrando a barra de progresso, Equipe 1 e Equipe 2]*

---

## 📂 Como Reproduzir este Projeto

1. Baixe o arquivo `solution/AgendamentoRadares.msapp`.
2. Acesse o [Power Apps Studio](https://make.powerapps.com).
3. Clique em **Abrir** > **Procurar arquivos** e selecione o `.msapp`.
4. Os esquemas e tabelas de exemplo estão documentados na pasta `/src`.
