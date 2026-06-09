# 🛡️ Nexus — Sistema de Resiliência de Conexão com Banco de Dados

<div align="center">

![Status](https://img.shields.io/badge/status-concluído-brightgreen)
![Stack](https://img.shields.io/badge/stack-HTML%20%2F%20CSS%20%2F%20JS-blue)
![Matéria](https://img.shields.io/badge/matéria-Interface%20e%20Jornada%20do%20Usuário-purple)

</div>

---

## 👨‍🏫 Informações Acadêmicas

| Campo | Informação |
|---|---|
| **Instituição** | UDF — Centro Universitário do Distrito Federal |
| **Curso** | Ciências da Computação |
| **Disciplina** | Interface e Jornada do Usuário |
| **Professor** | Leonardo Felipe Marinho Araujo |
| **Aluno(s)** | Gabriel Martins Sales — 43663435 |
| **Semestre** | 2026.1 |

---

## 📌 Sobre o Projeto

O **Nexus** é um sistema de resiliência de conexão com banco de dados que atua diretamente na camada de aplicação. Em vez de propagar erros imediatamente para a tela do usuário, ele aplica uma lógica inteligente de recuperação automática, tornando o sistema mais tolerante a falhas transitórias.

O mecanismo central é o **Retry com Exponential Backoff**: ao detectar uma falha de conexão, o sistema tenta se reconectar automaticamente com intervalos progressivos (1s → 2s → 4s → 8s), evitando sobrecarregar o banco e reduzindo ao máximo a necessidade de intervenção humana.

🔗 **Protótipo interativo (Figma):** [Acessar protótipo](https://www.figma.com/proto/UMW43Rm17DqLgLorqZqFTs/Semtítulo?node-id=1-4&t=WgXX6LJWkhuhL9nV-1)

---

## 🎯 Funcionalidades Principais

**Usuário Final:**
- Tela de lentidão — detecção de falha pela IA com aviso amigável
- Tela de reconexão — exibe o progresso das tentativas em tempo real
- Tela de resolução — confirmação de que tudo voltou ao normal

**DEV / DBA:**
- Dashboard de falhas — visão geral com métricas e eventos recentes
- Detalhes da falha — informações técnicas completas de cada incidente
- Configurações do Nexus — ajuste de parâmetros de retry (tempo, intensidade, número de tentativas)

---

## 👥 Perfis de Usuário

| Perfil | Acesso |
|---|---|
| Desenvolvedor | Detecção, retry, logs |
| DBA / DevOps | Monitoramento em tempo real, relatórios, configuração |
| Analista de Suporte | Consulta de logs e notificações |
| Usuário Final | Telas de status amigáveis (sem informações técnicas) |

---

## 📐 Diagramas UML

| Diagrama | Descrição |
|---|---|
| Casos de Uso | Interação de cada perfil com os recursos do sistema |
| Diagrama de Classes | Estrutura estática: tentativas de conexão, logs, parâmetros de retry e notificações |
| Diagrama de Atividades | Fluxo do mecanismo de Retry com Exponential Backoff |
| Diagrama de Sequência | Troca de mensagens entre usuário, aplicação, gerenciador de retry, banco de dados, log e notificação |

---

## ⚙️ Regras de Negócio

- Retentativas apenas para falhas **transitórias** (timeout, conexão recusada) — falhas permanentes como credenciais inválidas não disparam o retry
- Padrão de **4 tentativas** com intervalos 1s, 2s, 4s e 8s — configurável entre 1 e 10
- Alterações nos parâmetros de retry são registradas em **log de auditoria**
- Logs mantidos por no mínimo **90 dias**, sem permissão de exclusão manual por não-admins
- Notificação de falha crítica emitida **somente após esgotar todas as tentativas**
- Mensagens ao usuário final **sem detalhes técnicos** (sem stack trace, host ou código de erro)
- **Nenhuma string de conexão, senha ou token** é gravada nos logs

---

## 🚀 Como Rodar

Abra o `index.html` diretamente no navegador — sem dependências externas ou build necessário.

```bash
git clone https://github.com/seu-usuario/nexus.git
cd nexus
open index.html
```

---

## 📄 Referências

- NYGARD, Michael T. *Release It!: Design and Deploy Production-Ready Software*. 2. ed. Pragmatic Bookshelf, 2018.
- MICROSOFT. *Retry pattern*. Azure Architecture Center, 2023.
- DRAW.IO. *Diagrams.net: ferramenta de modelagem UML*. Disponível em: https://www.drawio.com
