# 🎛️Central de Projetos
## ⚡Projetos Ativos (Foco Atual)
*Apenas projetos que estou ativamente realizando no dia a dia*
```dataview
TABLE WITHOUT ID file.link AS "Projetos Ativos", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade", data_inicio AS "Data de Inicio"
FROM ""
WHERE tipo = "Projeto" AND status = "Ativo"
SORT prioridade DESC
```
## 💤  Incubadora (Projetos em Mente)
*Revisar esses projetos em pelo menos uma vez por semana*
```dataview
TABLE WITHOUT ID file.link AS "Projetos Futuros", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade Esperada", ultima_revisao AS "Data da Ultima Revisão"
FROM ""
WHERE tipo = "Projeto" AND status = "Incubadora"
SORT prioridade DESC
```
## 📦 Arquivo (Concluídos/esquecidos/abortado)
```dataview
TABLE WITHOUT ID file.link AS "Arquivados", status AS "Status", definicion_of_done AS "Objetivo Final (DoD)", prioridade AS "Prioridade Realizada", data_inicio AS "Data de Inicio", data_arquivamento AS "Data de Arquivo"
FROM ""
WHERE tipo = "Projeto" AND status = "Concluido" OR status = "Esquecido" OR status = "Abortado"
SORT prioridade DESC
```
