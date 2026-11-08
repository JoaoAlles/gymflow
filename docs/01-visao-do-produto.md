# Visão do Produto — GymFlow

## 1. Sobre o produto

O GymFlow é um sistema web de gestão desenvolvido para academias e studios, com o objetivo de centralizar informações administrativas e operacionais em uma única plataforma.

A proposta é facilitar o gerenciamento de alunos, planos, matrículas, frequência e informações financeiras, oferecendo uma visão organizada da operação.

O GymFlow será desenvolvido como um SaaS (Software as a Service), permitindo que diferentes academias utilizem a mesma plataforma, mantendo seus dados e configurações independentes.

## 2. Problema que o produto pretende resolver

Academias que possuem uma quantidade significativa de alunos enfrentam dificuldades para organizar e acompanhar informações cadastrais, financeiras e operacionais.

A falta de centralização dessas informações pode dificultar o acompanhamento dos alunos, o controle de pagamentos e a identificação de situações que exigem atenção da administração.

O GymFlow busca solucionar esses problemas por meio de uma plataforma centralizada, facilitando o acompanhamento da operação e a tomada de decisões.

## 3. Público-alvo

O GymFlow será inicialmente direcionado a pequenas e médias academias e studios de treinamento.

Os principais usuários previstos são:

- **Administradores:** responsáveis pela gestão geral da academia.
- **Recepcionistas:** responsáveis pelo atendimento, cadastro e acompanhamento dos alunos.
- **Professores:** responsáveis pelo acompanhamento das aulas e da frequência dos alunos.

## 4. Personalização por academia

Cada academia deverá possuir autonomia para configurar suas informações comerciais e operacionais.

Entre as configurações previstas estão:

- Nome da academia e informações cadastrais.
- Modalidades oferecidas.
- Nomes dos planos e opções comerciais.
- Valores e condições de contratação.
- Duração dos contratos.
- Periodicidade das cobranças.
- Períodos de ausência para alertas de frequência.
- Políticas de pausa de matrículas.
- Políticas de inadimplência.
- Tipos de alertas habilitados.

Cada academia deverá visualizar e administrar exclusivamente seus próprios dados, alunos, matrículas, planos, cobranças e configurações.

## 5. Prioridades do produto

O desenvolvimento do GymFlow terá como prioridade a organização e retenção de alunos.

A ordem inicial de importância será:

1. Identificação de alunos com planos próximos do vencimento.
2. Identificação de alunos com baixa frequência.
3. Acompanhamento de alunos inadimplentes.
4. Acompanhamento dos indicadores financeiros.

## 6. Regras de negócio

### 6.1. Planos próximos do vencimento

Alunos com matrícula ativa cujo contrato tenha vencimento previsto para os próximos 7 dias, incluindo o próprio dia do vencimento, devem ser identificados como próximos do vencimento.

O objetivo é permitir que a academia realize o acompanhamento e entre em contato para incentivar a renovação.

### 6.2. Baixa frequência

Alunos que já tenham registrado pelo menos uma presença e permaneçam sem comparecer pelo período configurado para sua modalidade devem ser identificados como alunos com baixa frequência.

Cada modalidade deverá possuir seu próprio período de ausência. Como referência inicial:

- Musculação: 10 dias.
- Natação: 20 dias.
- Crossfit: 12 dias.

Esses períodos poderão ser configurados pela administração.

A contagem deverá considerar cada matrícula e modalidade individualmente. Caso um aluno possua mais de uma modalidade, cada uma será monitorada separadamente.

O alerta deverá identificar o aluno e a modalidade em que foi constatada a baixa frequência.

O alerta permanecerá ativo enquanto não houver um novo registro de presença naquela modalidade. Ao registrar uma nova presença, o alerta será encerrado automaticamente.

### 6.3. Alunos que nunca iniciaram

Alunos com matrícula ativa que ainda não tenham registrado nenhuma presença deverão ser monitorados separadamente dos alunos com baixa frequência.

A contagem começa na data de início da matrícula. Caso o aluno alcance o período configurado para sua modalidade sem registrar nenhuma presença, deverá ser gerado um alerta específico chamado **"Nunca iniciou"**.

O alerta permanecerá ativo até que seja registrada a primeira presença.

Após a primeira presença, o aluno passará a ser acompanhado pela regra de baixa frequência.

### 6.4. Inadimplência

Alunos com matrícula ativa cuja data de vencimento de uma cobrança tenha sido ultrapassada, sem que o pagamento correspondente tenha sido registrado, devem ser identificados como inadimplentes.

O controle financeiro deverá considerar cada matrícula e suas respectivas cobranças.

Quando um plano incluir várias modalidades, a cobrança será vinculada à matrícula inteira, e não individualmente a cada modalidade.

Portanto, uma cobrança vencida poderá caracterizar inadimplência de toda a matrícula.

### 6.5. Múltiplas matrículas por aluno

Um aluno poderá possuir múltiplas matrículas, inclusive simultâneas.

Cada matrícula deverá manter seu próprio vínculo com um plano contratado, período de vigência, situação e histórico financeiro.

As regras de vencimento, frequência e inadimplência deverão considerar os vínculos correspondentes, sem duplicar o cadastro do aluno.

Uma mesma pessoa poderá possuir, por exemplo, uma matrícula de musculação e outra de natação.

### 6.6. Configuração dos alertas

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

## 7. Estrutura de planos e opções comerciais

### 7.1. Planos-base

O GymFlow deverá trabalhar com planos-base que representem os serviços oferecidos pela academia.

Cada plano-base poderá incluir uma ou várias modalidades.

Exemplos:

- Musculação.
- Natação.
- Plano Completo (Musculação, Natação e Crossfit).

Os nomes e as modalidades incluídas serão definidos pela própria academia.

### 7.2. Opções comerciais

Cada plano-base poderá possuir diferentes opções comerciais, com condições específicas de contratação.

Exemplos:

- Mensal.
- Semestral.
- Anual.
- Anual com pagamento à vista.

Cada opção comercial deverá permitir configurar:

- Duração contratual.
- Valor total do contrato.
- Valor e periodicidade das cobranças.
- Condições comerciais aplicáveis.

Os valores e as condições serão definidos pela academia.

A duração do contrato deverá ser independente da periodicidade de cobrança.

Por exemplo, um contrato anual poderá ter duração de 12 meses e cobrança mensal.

### 7.3. Alterações nos planos

Alterações realizadas no cadastro de um plano deverão afetar somente novas contratações.

Contratos já existentes deverão preservar as condições comerciais e as modalidades contratadas no momento da contratação.

O GymFlow deverá manter o histórico das condições originais de cada contratação, evitando que mudanças posteriores nos planos alterem contratos anteriores.

## 8. Matrículas e contratos

### 8.1. Contratação

A matrícula representa o vínculo comercial entre um aluno e um plano contratado.

Uma matrícula poderá incluir uma ou várias modalidades, conforme a opção comercial escolhida.

Cada matrícula deverá possuir suas próprias informações de contratação, vigência, situação e histórico financeiro.

### 8.2. Duração contratual e cobranças

A duração do contrato e a periodicidade das cobranças deverão ser tratadas separadamente.

Exemplos:

- Contrato mensal com cobrança mensal.
- Contrato semestral com cobrança mensal.
- Contrato anual com cobrança mensal.
- Contrato anual com pagamento único.

O GymFlow deverá permitir diferentes combinações de duração e periodicidade, conforme as opções comerciais cadastradas pela academia.

### 8.3. Renovações

A renovação deverá manter a matrícula existente, registrando um novo período contratado em seu histórico.

Cada período deverá preservar suas próprias datas de início e término e suas condições comerciais.

O objetivo é manter o histórico de permanência e renovações do aluno sem criar uma nova matrícula a cada renovação.

### 8.4. Pausas

O GymFlow deverá permitir que uma matrícula seja pausada temporariamente.

A pausa deverá preservar o vínculo existente e registrar:

- Data de início da pausa.
- Previsão de retorno.
- Motivo da pausa.
- Data efetiva de retorno.

Cada academia poderá configurar sua política de pausas, incluindo:

- Limite máximo de dias por pausa.
- Quantidade de pausas permitidas por contrato.
- Se as cobranças serão suspensas durante a pausa.
- Se o vencimento contratual será prorrogado.

A pausa não deverá apagar ou substituir o histórico financeiro e contratual.

### 8.5. Cancelamentos e novas contratações

Quando um aluno cancelar definitivamente sua matrícula, o vínculo deverá permanecer registrado como encerrado.

Caso o aluno retorne após o cancelamento, deverá ser criada uma nova matrícula, mantendo o histórico da matrícula anterior.

Uma pausa temporária não deverá ser tratada como cancelamento.

### 8.6. Estados da matrícula

A matrícula deverá permitir identificar diferentes situações, inicialmente:

- Ativa.
- Pausada.
- Cancelada.
- Encerrada por término contratual.

A inadimplência e o bloqueio de acesso deverão ser tratados separadamente da situação contratual da matrícula.

## 9. Alterações contratuais

### 9.1. Alteração de serviços e condições

O GymFlow deverá permitir alterações contratuais sem a necessidade de encerrar a matrícula existente.

Exemplo: um aluno que possui musculação poderá adicionar natação ao contrato.

Cada alteração deverá registrar:

- Data de vigência da alteração.
- Data em que a alteração foi registrada no sistema.
- Responsável pela alteração.
- Serviços anteriores e novos serviços contratados.
- Valores e condições anteriores e atualizados.

O histórico das condições anteriores deverá ser preservado.

### 9.2. Alterações retroativas

O GymFlow deverá permitir registrar alterações contratuais com data de vigência retroativa.

A academia poderá configurar um limite máximo de retroatividade, tendo 30 dias como referência inicial.

Alterações que ultrapassem esse limite deverão exigir permissão especial de um administrador.

Toda alteração deverá preservar a data efetiva de registro, a data de vigência e o responsável pela operação.

### 9.3. Cobranças decorrentes de alterações contratuais

Quando uma alteração contratual modificar o valor da contratação, a academia poderá configurar a política de cobrança aplicável.

As opções previstas são:

- Cobrança proporcional aos dias restantes do ciclo.
- Aplicação do novo valor somente no próximo ciclo de cobrança.
- Cobrança imediata da diferença integral.

A política aplicada deverá ser registrada no histórico da alteração contratual.

Mudanças futuras nas configurações da academia não deverão modificar cobranças já registradas.

## 10. Cobranças e inadimplência

### 10.1. Cobranças

Cada matrícula deverá possuir seu próprio histórico de cobranças.

Cada cobrança deverá registrar informações como:

- Valor.
- Data de vencimento.
- Data de pagamento, quando aplicável.
- Situação do pagamento.
- Período de referência.

O histórico de cobranças e pagamentos deverá ser preservado.

### 10.2. Consequências da inadimplência

A identificação de inadimplência não deverá significar cancelamento automático da matrícula.

Cada academia poderá configurar suas políticas de inadimplência, incluindo:

- Quantidade de dias de atraso para bloquear o acesso.
- Se o bloqueio será aplicado a todas as modalidades ou somente a algumas.
- Quantidade de dias de atraso para permitir o cancelamento.
- Se o cancelamento será automático ou dependerá de uma ação administrativa.

O bloqueio de acesso, a inadimplência e o cancelamento contratual deverão ser tratados como situações distintas.

Nenhuma dessas operações deverá apagar o histórico financeiro ou contratual do aluno.

## 11. Diretrizes de histórico e rastreabilidade

O GymFlow deverá preservar o histórico das operações importantes realizadas no sistema.

Alterações contratuais, renovações, pausas, cancelamentos, cobranças e pagamentos deverão manter seus registros históricos.

Sempre que aplicável, as operações deverão identificar o responsável e as datas de ocorrência e registro.

O objetivo é permitir consultas futuras, auditorias e relatórios confiáveis, sem perda de informações anteriores.

## 12. Usuários, permissões e segurança

### 12.1. Acesso a múltiplas academias

- Um mesmo usuário poderá acessar várias academias utilizando uma única conta.
- Cada usuário terá um vínculo independente com cada academia.
- Cada vínculo poderá possuir diferentes perfis de acesso.
- As permissões serão determinadas pelos perfis atribuídos em cada academia.

### 12.2. Seleção da academia após o login

- Após autenticar o usuário, o sistema deverá consultar suas academias com acesso ativo.
- Se houver apenas uma academia, o acesso será direcionado automaticamente.
- Se houver mais de uma academia, o sistema deverá apresentar uma tela de seleção.
- Somente academias com vínculo ativo serão exibidas.
- O usuário poderá trocar de academia posteriormente, sem precisar realizar logout.
- As permissões deverão ser carregadas conforme a academia selecionada.

### 12.3. Perfis de acesso

A primeira versão utilizará perfis predefinidos:

- **Administrador:** acesso administrativo completo à própria academia.
- **Recepcionista:** gerenciamento operacional de alunos, matrículas, pagamentos e frequência.
- **Professor:** acesso limitado às atividades, turmas, modalidades e alunos sob sua responsabilidade.

Um usuário poderá possuir mais de um perfil na mesma academia.

As permissões serão combinadas conforme os perfis atribuídos.

A personalização de permissões ficará para uma evolução futura.

### 12.4. Convites de usuários

- O administrador poderá convidar funcionários informando o e-mail e selecionando os perfis de acesso.
- Se o e-mail não possuir uma conta, o convidado deverá criar sua conta e senha.
- Se já possuir uma conta, poderá aceitar o vínculo com a nova academia utilizando a conta existente.
- O acesso somente será liberado após a aceitação do convite.
- Convites poderão ter os estados pendente, aceito ou expirado.
- O administrador poderá reenviar ou cancelar convites.

### 12.5. Remoção e desativação de acessos

- O administrador poderá desativar o vínculo de um usuário com sua academia.
- A desativação deverá retirar imediatamente o acesso àquela academia.
- A conta global do usuário permanecerá ativa.
- Os acessos do usuário a outras academias não serão afetados.
- Os registros históricos associados ao usuário deverão ser preservados.
- A remoção de acesso não deverá provocar exclusão física dos registros relacionados.

### 12.6. Alteração de permissões

Somente administradores da respectiva academia poderão:

- Enviar e cancelar convites.
- Adicionar ou remover perfis.
- Desativar ou reativar vínculos.
- Consultar os usuários vinculados à academia.

Todas essas operações deverão gerar registros na auditoria.

### 12.7. Proteção do último administrador

Cada academia deverá possuir pelo menos um administrador ativo.

O sistema deverá impedir:

- Desativação do último administrador.
- Remoção do perfil de administrador do último usuário que o possui.
- Exclusão do vínculo do último administrador.
- Qualquer operação que deixe a academia sem administrador ativo.

Outro usuário deverá ser promovido a administrador antes da realização dessas operações.

### 12.8. Recuperação administrativa

Caso uma academia perca o acesso ao seu único administrador, deverá existir um procedimento de recuperação controlado pela administração geral do GymFlow.

O procedimento deverá:

- Exigir solicitação formal.
- Validar a identidade e a legitimidade do solicitante.
- Permitir recuperação ou transferência do acesso administrativo após aprovação.
- Registrar todas as etapas na auditoria.

### 12.9. Administração geral do GymFlow

A plataforma terá um nível administrativo independente, denominado **Superadministrador GymFlow**.

Esse perfil será responsável por:

- Cadastrar, suspender e reativar academias.
- Gerenciar a administração geral da plataforma.
- Prestar suporte técnico.
- Realizar procedimentos de recuperação administrativa.
- Gerenciar questões de segurança.
- Consultar informações necessárias para auditoria e suporte.

O superadministrador não dependerá dos perfis administrativos das academias.

Seu acesso a informações das academias deverá respeitar controles de segurança, justificativa e auditoria.

### 12.10. Acesso para suporte técnico

Quando um superadministrador precisar acessar uma academia para prestar suporte:

- Deverá informar o motivo do acesso.
- Deverá identificar a academia envolvida.
- O sistema deverá identificar o superadministrador responsável.
- Deverá registrar o início e o término do acesso.
- Todas as ações realizadas deverão ser registradas na auditoria.

### 12.11. Auditoria e preservação histórica

O GymFlow terá um sistema centralizado de auditoria.

As operações relevantes deverão registrar:

- Usuário responsável.
- Academia relacionada.
- Ação realizada.
- Registro afetado.
- Data e horário.
- Valores anteriores e posteriores, quando aplicável.

A auditoria deverá contemplar alterações cadastrais, financeiras, administrativas, contratuais, permissões, acessos e tratamento de alertas.

Regras de acesso:

- Administradores poderão consultar a auditoria completa de sua própria academia.
- Recepcionistas e professores não terão acesso à auditoria completa.
- Superadministradores poderão consultar a auditoria global para suporte e segurança.

Os registros de auditoria não poderão ser alterados ou excluídos por administradores comuns.

A remoção de usuários não poderá apagar ou comprometer os registros históricos de suas ações.