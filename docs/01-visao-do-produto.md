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

### 1. Planos próximos do vencimento

Alunos com matrícula ativa cujo plano tenha vencimento previsto para os próximos 7 dias, incluindo o próprio dia do vencimento, devem ser identificados como próximos do vencimento.

O objetivo é permitir que a academia realize o acompanhamento e entre em contato para incentivar a renovação.

### 2. Baixa frequência

Alunos que já tenham registrado pelo menos uma presença e permaneçam sem comparecer pelo período configurado para sua modalidade devem ser identificados como alunos com baixa frequência.

Cada modalidade deverá possuir seu próprio período de ausência. Como referência inicial:

- Musculação: 10 dias.
- Natação: 20 dias.
- Crossfit: 12 dias.

Esses períodos poderão ser configurados futuramente pela administração.

A contagem deverá considerar cada matrícula individualmente. Caso um aluno possua mais de uma modalidade, cada uma será monitorada separadamente.

O alerta deverá identificar o aluno e a modalidade em que foi constatada a baixa frequência.

O alerta permanecerá ativo enquanto não houver um novo registro de presença naquela modalidade. Ao registrar uma nova presença, o alerta será encerrado automaticamente.

### 3. Alunos que nunca iniciaram

Alunos com matrícula ativa que ainda não tenham registrado nenhuma presença deverão ser monitorados separadamente dos alunos com baixa frequência.

A contagem começa na data de início da matrícula. Caso o aluno alcance o período configurado para sua modalidade sem registrar nenhuma presença, deverá ser gerado um alerta específico chamado **"Nunca iniciou"**.

O alerta permanecerá ativo até que seja registrada a primeira presença.

Após a primeira presença, o aluno passará a ser acompanhado pela regra de baixa frequência.

### 4. Inadimplência

Alunos com matrícula ativa cuja data de vencimento da mensalidade tenha sido ultrapassada, sem que o pagamento correspondente tenha sido registrado, devem ser identificados como inadimplentes.

O objetivo é permitir que a administração acompanhe os pagamentos pendentes e realize ações de cobrança.

O controle financeiro deverá considerar cada matrícula e suas respectivas cobranças, permitindo que um aluno possua pagamentos pendentes em uma modalidade e esteja em dia em outra.

### 5. Múltiplas matrículas por aluno

Um aluno poderá possuir múltiplas matrículas, inclusive simultâneas.

Cada matrícula deverá manter seu próprio vínculo com um plano ou modalidade, período de vigência, situação e histórico financeiro.

As regras de vencimento, frequência e inadimplência deverão considerar os vínculos correspondentes, sem duplicar o cadastro do aluno.

### 6. Configuração dos alertas

O GymFlow deverá permitir que a administração ative ou desative individualmente cada tipo de alerta.

Por padrão, todos os alertas deverão vir ativados.

Os tipos de alerta previstos inicialmente são:

- Planos próximos do vencimento.
- Baixa frequência.
- Nunca iniciou.
- Inadimplência.

Os períodos de ausência para os alertas de frequência também deverão poder ser configurados individualmente por modalidade.

Quando um tipo de alerta for desativado:

- Os alertas já existentes deverão permanecer visíveis.
- O sistema não deverá gerar novos alertas daquele tipo enquanto estiver desativado.
- Os alertas existentes continuarão seguindo suas regras normais de encerramento.

Ao reativar um tipo de alerta, o sistema deverá voltar a monitorar as condições correspondentes e gerar alertas quando aplicável.