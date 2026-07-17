# 🎛️ Central de Projetos - Obsidian Vault

Este repositório contém a estrutura e o fluxo de trabalho do meu sistema de gerenciamento de projetos no Obsidian. O objetivo deste Vault é rastrear o ciclo de vida de projetos desde a concepção (Incubadora) até a execução (Ativos) e finalização (Arquivo), utilizando metadados e consultas automatizadas.

---

## 🛠️ Tecnologias e Plugins Essenciais

Para que o sistema funcione exatamente como projetado, as seguintes configurações estão em uso:
*   **Plugin:** Dataview (Obrigatório para as automações e lembre-se de ativar o javaquery nas configurações do plugin).
*   **Temas:** Suporte configurado para *Things* e *Obsidianite*.

---

## 📁 Arquitetura do Sistema

A organização de pastas foi mantida enxuta. Os projetos ficam na raiz ou separados por contexto, enquanto a pasta `Sistema` guarda a lógica de templates.

```
Vault Obsidian - Projetos/
├── .obsidian/               # Configurações do Obsidian, plugins e temas
│   ├── plugins/
│   │   └── dataview/
│   └── themes/
│       ├── Obsidianite/
│       └── Things/
├── projeto_Estudos_Dio/     # Exemplo de projeto de estudos
├── projeto_Trocar_de_Emprego/ # Exemplo de projeto ativo
└── Sistema/                 # Templates e arquivos estruturais
```
---
⚙️ Estrutura de Metadados (Dataview)
Cada projeto criado neste Vault precisa conter o seguinte cabeçalho de propriedades no formato YAML. É este cabeçalho que alimenta os painéis de controle.
```
tipo: Projeto
status: # Ativo | Incubadora | Concluido | Esquecido | Abortado
prioridade: # Alta | Media | Baixa
tags: 
definicion_of_done: 
data_inicio: 
data_arquivamento: 
data_revisao: 
```
---
## 📊 Painéis de Controle (Dataview Queries)
O gerenciamento diário é feito através de um painel central que divide os projetos em três categorias de foco. 
(Importante: não esqueça de adicionar **dataview** após os ```).

### ⚡ Projetos Ativos (Foco Atual)
Lista apenas os projetos em execução no dia a dia.
```dataview
TABLE WITHOUT ID file.link AS "Projetos Ativos", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade", data_inicio AS "Data de Inicio"
FROM ""
WHERE tipo = "Projeto" AND status = "Ativo"
SORT prioridade DESC
```
### 💤 Incubadora (Projetos em Mente)
Ideias e projetos futuros que devem ser revisados pelo menos uma vez por semana.
```dataview
TABLE WITHOUT ID file.link AS "Projetos Futuros", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade Esperada", ultima_revisao AS "Data da Ultima Revisão"
FROM ""
WHERE tipo = "Projeto" AND status = "Incubadora"
SORT prioridade DESC
```
### 📦 Arquivo
Histórico do que já foi feito, cancelado ou abandonado.

```dataview
TABLE WITHOUT ID file.link AS "Arquivados", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade Realizada", data_inicio AS "Data de Inicio", data_arquivamento AS "Data de Arquivo"
FROM ""
WHERE tipo = "Projeto" AND status = "Concluido" OR status = "Esquecido" OR status = "Abortado"
SORT prioridade DESC
```
## 🚀 Como Utilizar

1. Faça o clone deste repositório na sua máquina local.
2. Abra o **Obsidian** e selecione "Open folder as vault" na pasta clonada.
3. Garanta que o plugin **Dataview** está ativado nas configurações (`Settings > Community Plugins`).
4. Para criar um novo projeto, copie a estrutura de Frontmatter no topo de uma nova nota e defina o campo `tipo` como `Projeto`.
