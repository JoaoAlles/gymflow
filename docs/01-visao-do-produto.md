# Visão do Produto — GymFlow

## Sobre o produto

O GymFlow é um sistema web de gestão desenvolvido para academias e studios, com o objetivo de centralizar informações administrativas e operacionais em uma única plataforma.

A proposta é facilitar o gerenciamento de alunos, planos, matrículas, frequência e informações financeiras, oferecendo uma visão organizada da operação.

## Problema que o produto pretende resolver

Academias que possuem uma quantidade significativa de alunos enfrentam dificuldades para organizar e acompanhar informações cadastrais, financeiras e operacionais.

A falta de centralização dessas informações pode dificultar o acompanhamento dos alunos, o controle de pagamentos e a identificação de situações que exigem atenção da administração.

O GymFlow busca solucionar esses problemas por meio de uma plataforma centralizada, facilitando o acompanhamento da operação e a tomada de decisões.

## Público-alvo

O GymFlow será inicialmente direcionado a pequenas e médias academias e studios de treinamento.

Os principais usuários previstos são:

- **Administradores:** responsáveis pela gestão geral da academia.
- **Recepcionistas:** responsáveis pelo atendimento, cadastro e acompanhamento dos alunos.
- **Professores:** responsáveis pelo acompanhamento das aulas e da frequência dos alunos.

## Prioridades do produto

O desenvolvimento do GymFlow terá como prioridade a organização e retenção de alunos.

A ordem inicial de importância será:

1. Identificação de alunos com planos próximos do vencimento.
2. Identificação de alunos com baixa frequência.
3. Acompanhamento de alunos inadimplentes.
4. Acompanhamento dos indicadores financeiros.

## Regras de negócio

1. Alunos ativos cujo plano tenha vencimento previsto para os próximos 7 dias, incluindo o próprio dia do vencimento, devem ser identificados como próximos do vencimento. O objetivo é permitir que a academia realize o acompanhamento e entre em contato para incentivar a renovação.

2. Alunos com matrícula ativa que permaneçam 10 dias consecutivos ou mais sem registrar uma entrada na academia devem ser identificados como alunos com baixa frequência. O objetivo é permitir que a administração identifique possíveis riscos de cancelamento e realize um contato preventivo.

3. Alunos com matrícula ativa cuja data de vencimento da mensalidade tenha sido ultrapassada, sem que o pagamento tenha sido registrado, devem ser identificados como inadimplentes. O objetivo é permitir que a administração acompanhe os pagamentos pendentes e realize ações de cobrança.