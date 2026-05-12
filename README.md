# Automação RPA — Plataforma de Integração de Chamados

## Related Projects

🔒 Private Repository: `https://github.com/EveMurta/MS_Power_Automate_Integracao_JIRA-ASSIST`

## 📌 Visão Geral

Esta automação integra uma plataforma de chamados com Microsoft Power Platform e um fluxo de automação desktop (RPA). A solução automatiza o monitoramento, coleta, roteamento e processamento assistido de chamados técnicos provenientes de grupos operacionais específicos.

O fluxo realiza:

* Monitoramento periódico de chamados via integração REST API.
* Identificação de novos incidentes e reaberturas.
* Armazenamento das informações em uma planilha online colaborativa.
* Execução condicional de um robô desktop para processamento assistido.

A arquitetura combina automação em nuvem e automação desktop para reduzir esforço operacional manual e acelerar o tempo de resposta dos atendimentos.

---

## 🎯 Objetivos

* Automatizar o monitoramento de chamados técnicos.
* Eliminar verificações manuais de filas operacionais.
* Manter uma base centralizada de incidentes.
* Acionar automações desktop sob demanda.
* Reduzir tempo de resposta e retrabalho operacional.

---

## 🛠 Tecnologias Utilizadas

* Power Automate / Azure Logic Apps
* Integração REST API
* Excel Online (Business)
* Power Automate Desktop (RPA)
* Microsoft Power Platform
* Automação em Nuvem e Desktop

---

## 🔄 Fluxo do Processo

```text
Gatilho Agendado
    ↓
Requisição REST API
    ↓
Percorre incidentes retornados
    ↓
Valida se incidente já existe
    ├── Não → Cria novo registro
    │          Aciona automação desktop
    └── Sim → Verifica reabertura
               ├── Reaberto hoje → Novo registro
               └── Caso contrário → Ignora
    ↓
Executa fluxo desktop
```

---

## 📂 Estrutura de Armazenamento

A automação utiliza uma planilha online como fila operacional.

### Campos utilizados

| Campo                | Descrição                  |
| -------------------- | -------------------------- |
| ID Loja              | Identificador da unidade   |
| Solicitante          | Responsável pelo chamado   |
| Resumo               | Título do incidente        |
| Fila                 | Grupo operacional          |
| Incidente            | Código do chamado          |
| Descrição            | Detalhamento do chamado    |
| Status Processamento | Indicador de processamento |
| Contato              | Informações de contato     |
| Status               | Situação atual             |
| Data/Hora            | Timestamp da inserção      |

---

## ⚙️ Configuração de Ambiente

### Parâmetros

| Parâmetro        | Descrição                                  |
| ---------------- | ------------------------------------------ |
| Modo de Execução | Define execução assistida ou não assistida |

### Integrações

* Conexão com planilha online
* Conexão com automação desktop
* Integração via API REST

---

## 🧩 Principais Componentes

### Fluxo em Nuvem

| Componente             | Função                               |
| ---------------------- | ------------------------------------ |
| Gatilho Agendado       | Executa periodicamente               |
| Requisição API         | Consulta incidentes                  |
| Validação de Registros | Verifica existência do chamado       |
| Regras Condicionais    | Trata novos incidentes e reaberturas |
| Disparo RPA            | Executa automação desktop            |

### Fluxo Desktop

Responsável por:

* Processar incidentes pendentes
* Executar tarefas operacionais assistidas
* Atualizar registros
* Finalizar processamento

---

## 📊 Regras de Negócio

### Seleção de Chamados

* Apenas incidentes ativos são processados.
* Filas operacionais específicas são monitoradas.
* Chamados são ordenados por data de criação.

### Lógica de Processamento

| Situação             | Ação                             |
| -------------------- | -------------------------------- |
| Novo incidente       | Cria registro e aciona automação |
| Incidente reaberto   | Cria novo processamento          |
| Incidente já tratado | Ignora                           |

---

## 🚨 Tratamento de Erros

Implementação atual:

* O fluxo é interrompido caso uma dependência falhe.
* Não há política de retry ou notificação automática.

Melhorias futuras possíveis:

* Retry automático
* Alertas operacionais
* Logs estruturados
* Observabilidade

---

## 🔧 Dependências

* Permissões de acesso à API
* Permissões de acesso à planilha
* Ambiente RPA configurado
* Licenciamento Power Platform
* Agente de automação desktop instalado

---

## 🖥 Requisitos de Infraestrutura

* Ambiente Windows
* Power Automate Desktop instalado
* Fluxos desktop publicados
* Permissões adequadas de execução

---

## 👥 Times Envolvidos

* Time de Automação em Nuvem
* Time de RPA
* Time Operacional
* Segurança da Informação

---

## 📄 Licença

Uso interno corporativo.

