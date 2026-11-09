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

## 13. Cadastro e gerenciamento de alunos

### 13.1. Independência entre academias

- Cada academia terá seus próprios cadastros de alunos.
- Não haverá compartilhamento de identidade ou histórico de alunos entre academias.
- O mesmo CPF poderá existir em academias diferentes.
- Dados pessoais, matrículas, pagamentos, frequência e histórico serão independentes por academia.

### 13.2. Dados cadastrais

O cadastro inicial do aluno terá os seguintes campos:

| Campo              | Obrigatoriedade |
| Nome completo      | Obrigatório |
| CPF                | Obrigatório |
| Data de nascimento | Obrigatório |
| Telefone           | Obrigatório |
| E-mail             | Opcional |
| Endereço           | Opcional |
| Foto               | Opcional |

### 13.3. Validação do CPF

- O CPF deverá possuir 11 dígitos.
- O sistema deverá validar matematicamente os dígitos verificadores.
- O CPF deverá ser único dentro de cada academia.
- O sistema deverá impedir cadastros duplicados na mesma academia.
- O mesmo CPF poderá existir em academias diferentes.
- A alteração do CPF deverá respeitar a regra de unicidade.

A validação deverá existir no frontend, backend e banco de dados.

### 13.4. Situação cadastral

O cadastro do aluno terá os seguintes estados:

- **Ativo:** cadastro disponível para operações normais.
- **Inativo:** cadastro preservado, mas sem utilização operacional normal.
- **Arquivado:** cadastro preservado para consulta histórica, sem utilização em novas operações.

A situação cadastral será independente da situação das matrículas.

Um aluno poderá possuir um cadastro ativo mesmo sem matrículas ativas.

Não será permitido arquivar um aluno enquanto possuir matrículas ativas ou pausadas. Essas matrículas deverão ser encerradas ou canceladas previamente.

### 13.5. Responsáveis e dependentes

O GymFlow permitirá cadastrar responsáveis e dependentes.

- Cada pessoa terá seu próprio cadastro e CPF.
- Um responsável poderá possuir vários dependentes.
- Cada dependente poderá possuir suas próprias matrículas.
- Frequência, alertas e histórico serão individuais.
- O responsável poderá assumir pagamentos das matrículas dos dependentes.
- A inativação ou remoção do responsável não poderá apagar os registros dos dependentes.

### 13.6. Responsabilidade financeira

Cada matrícula terá um único responsável financeiro.

- O responsável poderá ser o próprio aluno.
- Um responsável poderá pagar matrículas de diferentes alunos.
- Um aluno poderá possuir responsáveis financeiros diferentes em matrículas distintas.
- A responsabilidade financeira não altera a titularidade da matrícula.
- Cobranças, pagamentos e inadimplência permanecerão vinculados à matrícula correspondente.
- A alteração do responsável financeiro será permitida e deverá gerar histórico e auditoria.
- Não haverá divisão de cobranças entre responsáveis na primeira versão.
- A possibilidade de múltiplos responsáveis financeiros ficará para uma evolução futura.

### 13.7. Responsável legal

O cadastro permitirá identificar um ou mais responsáveis legais, quando aplicável.

- Menores de 18 anos deverão possuir pelo menos um responsável legal cadastrado.
- Maiores de 18 anos poderão possuir responsáveis legais, mas o cadastro será opcional.
- O cadastro de um segundo responsável legal também será opcional.
- Todos os responsáveis legais ativos receberão as comunicações não financeiras destinadas aos responsáveis.
- A remoção de um responsável não apagará o histórico dos vínculos e comunicações anteriores.

### 13.8. Contatos autorizados e comunicações

As comunicações serão direcionadas conforme a natureza da informação.

**Comunicações financeiras:**
- Mensalidades e cobranças.
- Pagamentos confirmados.
- Inadimplência.
- Reajustes e alterações financeiras.

Essas comunicações serão destinadas ao responsável financeiro.

**Comunicações não financeiras:**
- Frequência e ausências.
- Alertas de baixa frequência.
- Comunicados da academia.
- Emergências.
- Informações sobre atividades.

Para menores de 18 anos, serão destinadas aos responsáveis legais. Para maiores de 18 anos, serão destinadas diretamente ao aluno.

Se a mesma pessoa exercer as funções de responsável legal e financeiro, receberá ambas as categorias.

Quando um aluno maior de idade não possuir responsável financeiro, as comunicações financeiras serão destinadas a ele.

Quando um menor não possuir responsável legal cadastrado, o sistema deverá sinalizar a pendência para a academia.

Contatos autorizados poderão ser cadastrados para situações específicas, como retirada de menores, conforme regras que serão detalhadas posteriormente.

### 13.9. Transição para maioridade

Quando o aluno completar 18 anos:

- As comunicações não financeiras passarão automaticamente a ser destinadas ao próprio aluno.
- Os responsáveis legais deixarão de receber essas comunicações automaticamente.
- O responsável financeiro permanecerá vinculado até que seja alterado.
- A academia receberá uma notificação para revisar os dados dos responsáveis.
- O histórico dos vínculos e comunicações anteriores será preservado.
- A transição não modificará contratos, matrículas ou cobranças existentes.

### 13.10. Documentos e autorizações

O GymFlow terá um módulo de documentos e autorizações dos alunos.

Cada documento poderá possuir:

- Nome e tipo do documento.
- Arquivo anexado.
- Data de emissão.
- Data de validade, quando aplicável.
- Status: válido, pendente, vencido ou dispensado.
- Responsável pelo envio.
- Histórico de alterações e versões.

Exemplos:

- Atestado médico.
- Termo de responsabilidade.
- Autorização para prática de atividades físicas.
- Autorização dos responsáveis para menores.

### 13.11. Exigências documentais por academia e modalidade

- Cada academia poderá configurar suas próprias exigências documentais.
- As exigências poderão variar conforme a modalidade.
- Um documento poderá ser obrigatório ou opcional.
- Poderá existir prazo de validade.
- Alterações nas exigências não apagarão documentos ou históricos anteriores.

Um mesmo documento poderá atender às exigências de várias modalidades da mesma academia, desde que cumpra os requisitos de cada uma.

A validade será controlada pelo documento original. Quando ele vencer, todas as modalidades que dependem dele deverão ser sinalizadas.

A substituição do arquivo deverá preservar o histórico da versão anterior.

### 13.12. Comportamento diante de documentos pendentes ou vencidos

Cada academia poderá configurar o comportamento de cada exigência documental:

1. Apenas alertar sobre a pendência.
2. Impedir novas matrículas até a regularização.
3. Impedir a frequência na modalidade relacionada até a regularização.

O bloqueio deverá afetar somente as modalidades que exigem o documento, não necessariamente todas as atividades do aluno.

O sistema deverá manter histórico dos bloqueios, regularizações e alterações das regras.

### 13.13. Permissões para documentos

- **Administrador:** configura exigências, gerencia e consulta todos os documentos.
- **Recepcionista:** cadastra, envia, atualiza e consulta documentos completos.
- **Professor:** consulta somente a situação documental dos alunos vinculados às suas atividades.

Professores não poderão abrir arquivos pessoais, como atestados médicos e outros documentos completos.

Operações relevantes envolvendo documentos deverão ser registradas na auditoria.

### 13.14. Armazenamento e segurança documental

- Os arquivos serão armazenados de forma privada, sem links públicos.
- O acesso será validado pelo sistema conforme as permissões do usuário.
- O banco de dados armazenará metadados e referências aos arquivos, não o conteúdo binário.
- Visualizações e downloads exigirão autorização.
- Substituições e exclusões deverão preservar o histórico necessário.
- O acesso aos documentos deverá ser rastreável pela auditoria.
- O sistema deverá validar formato, tamanho e segurança dos arquivos enviados.

### 13.15. Histórico cadastral

Alterações nos dados pessoais do aluno deverão preservar o histórico dos valores anteriores.

O sistema deverá registrar:

- Campo alterado.
- Valor anterior.
- Novo valor.
- Usuário responsável pela alteração.
- Academia relacionada.
- Data e horário da alteração.

O histórico deverá permitir consultar alterações anteriores e identificar quem realizou cada operação.

A preservação histórica deverá respeitar as regras de segurança, privacidade e retenção de dados aplicáveis.

## 14. Matrículas e contratos

### 14.1 Datas da matrícula

Toda matrícula deverá possuir três datas independentes:

- **Data da contratação:** data em que a venda e a contratação foram realizadas.
- **Data de início:** data em que começa a vigência do contrato e o aluno passa a ter direito de utilizar os serviços contratados.
- **Data de término:** calculada com base na duração contratual e na data de início.

O sistema deverá permitir que a data de início seja posterior à data da contratação.

Exemplo:
- Contratação: 08/11/2026.
- Início da vigência: 01/12/2026.
- Término: 30/11/2027, considerando um contrato de 12 meses.

Matrículas com início futuro deverão permanecer registradas no sistema, mas não poderão liberar frequência antes do início da vigência.

### 14.2 Status de matrícula agendada

Quando a data de início for futura, a matrícula deverá receber o status **Agendada**.

A matrícula agendada:
- Já estará vinculada ao aluno e ao plano contratado.
- Deverá aparecer nas consultas e relatórios administrativos.
- Não permitirá registro de frequência antes do início da vigência.
- Passará automaticamente para o status Ativa na data de início, desde que não exista outra condição que impeça sua ativação.

O status Agendada não deverá ser confundido com matrícula Pausada ou Inativa.

### 14.3 Regra de início da cobrança

Cada academia poderá configurar quando a primeira cobrança de uma matrícula deverá ser gerada:

- **Na contratação:** a primeira cobrança será gerada na data da contratação, mesmo que o início da vigência seja futuro.
- **No início da vigência:** a primeira cobrança será gerada quando o contrato começar.

A regra selecionada deverá ser registrada na matrícula e preservada durante todo o histórico contratual.

Alterações futuras nas configurações da academia não deverão modificar as condições de cobrança de matrículas já contratadas.

### 14.4 Dia de vencimento das cobranças

Cada matrícula poderá utilizar uma das seguintes regras de vencimento:

- **Baseado na data de início:** o vencimento mensal ocorrerá no mesmo dia em que a matrícula iniciou sua vigência.
- **Dia fixo da academia:** o vencimento ocorrerá em um dia específico definido pela academia, podendo variar entre matrículas.

A regra e o dia de vencimento escolhidos deverão ser registrados nas condições financeiras da matrícula.

Alterações futuras nas configurações da academia não deverão modificar automaticamente as condições de matrículas existentes.

### 14.5 Primeiro período de cobrança

Quando a data de início da matrícula não coincidir com o dia de vencimento definido, a academia poderá configurar como será realizada a primeira cobrança:

- **Cobrança proporcional:** o sistema calculará o valor proporcional aos dias entre o início da vigência e o próximo vencimento.
- **Cobrança integral:** será cobrado o valor mensal completo, independentemente da quantidade de dias do primeiro período.

A regra aplicada deverá ser registrada na matrícula e preservada no histórico financeiro.

Alterações futuras nas configurações da academia não deverão modificar cobranças já geradas ou condições financeiras de matrículas existentes.

### 14.6 Vencimento em dias inexistentes no mês

Quando o dia de vencimento configurado não existir em determinado mês, a academia poderá escolher entre:

- **Antecipar:** utilizar o último dia do mês.
- **Postergar:** utilizar o primeiro dia do mês seguinte.

Exemplo: uma matrícula com vencimento no dia 31 terá seu vencimento em 28 ou 29 de fevereiro, conforme a regra de antecipação, ou em 1º de março, conforme a regra de postergação.

A regra escolhida deverá ser registrada nas condições financeiras da matrícula e preservada para o histórico contratual.

### 14.7 Vencimentos em finais de semana e feriados

A academia poderá configurar como o sistema deverá tratar vencimentos que coincidam com sábados, domingos ou feriados:

- **Manter a data original:** o vencimento permanece na data inicialmente calculada.
- **Próximo dia útil:** o vencimento será transferido automaticamente para o próximo dia útil.

A identificação de feriados deverá considerar, futuramente, os calendários nacionais, estaduais e municipais correspondentes à localização da academia.

A regra escolhida deverá ser registrada nas condições financeiras da matrícula e aplicada aos vencimentos futuros, sem alterar cobranças já geradas.

### 14.8 Alterações nas condições financeiras durante a renovação

Durante a renovação de uma matrícula, a academia poderá revisar e alterar as condições financeiras do novo período contratual, incluindo:

- Dia e modelo de vencimento.
- Política de cobrança do primeiro período.
- Tratamento de vencimentos em dias inexistentes no mês.
- Tratamento de vencimentos em finais de semana e feriados.
- Valores e demais condições comerciais do novo contrato.

As novas condições serão aplicadas exclusivamente ao período renovado.

O período contratual anterior deverá preservar integralmente suas condições originais, cobranças e histórico financeiro.

### 14.9 Renovação automática de matrículas

Cada academia poderá configurar se as matrículas terão renovação automática, sendo essa opção habilitada por padrão.

Quando a renovação automática estiver habilitada:
- Ao término do período contratual, o sistema deverá gerar um novo período para a mesma matrícula.
- O histórico dos períodos anteriores deverá ser preservado.
- A matrícula continuará vinculada ao mesmo aluno.
- As condições do novo período deverão ser registradas individualmente.

Quando a renovação automática estiver desabilitada:
- Ao término do período contratual, a matrícula deverá mudar automaticamente para o status Encerrada.
- O cadastro do aluno e todo o histórico da matrícula deverão ser preservados.

A configuração deverá ser respeitada pelo sistema sem alterar períodos contratuais anteriores.  

### 14.10 Política de preços na renovação automática

A academia poderá configurar como os preços serão tratados durante as renovações automáticas:

- **Manter preço anterior:** o novo período contratual preservará o valor praticado no período anterior.
- **Aplicar preço vigente:** o novo período utilizará o preço atualmente configurado para o plano na data da renovação.

A política aplicada, o valor anterior e o novo valor deverão ser registrados no histórico contratual.

Alterações futuras nos preços ou nas configurações da academia não deverão modificar períodos contratuais anteriores nem cobranças já geradas.

### 14.11 Comunicação de reajuste na renovação automática

Quando uma renovação automática resultar em aumento de preço, o sistema deverá comunicar o aluno ou responsável financeiro antes da aplicação do novo valor.

A academia poderá configurar a antecedência mínima da comunicação.

O registro da comunicação deverá conter:
- Data prevista da renovação.
- Valor anterior e novo valor.
- Data e horário do envio.
- Destinatário.
- Canal utilizado.
- Status do envio.

Caso a comunicação não possa ser enviada, o sistema deverá registrar a falha e gerar um alerta para a equipe da academia.

O histórico das comunicações deverá ser preservado.

### 14.12 Recusa de reajuste e cancelamento da renovação

Quando uma renovação automática resultar em aumento de preço, o aluno ou responsável financeiro poderá solicitar o cancelamento da renovação antes da aplicação do novo valor.

A academia poderá configurar o prazo máximo para essa solicitação, contado a partir da comunicação do reajuste.

Quando o cancelamento for solicitado dentro do prazo:
- A renovação automática deverá ser cancelada.
- O contrato atual permanecerá válido até o término de sua vigência.
- A matrícula será encerrada ao final do período contratual.
- Não poderá ser aplicada multa por fidelidade decorrente da recusa ao novo período contratual.

As obrigações financeiras e contratuais já existentes no período vigente deverão ser preservadas.

O sistema deverá registrar a solicitação, a data, o responsável e o cancelamento da renovação no histórico da matrícula.

### 14.13 Renovação automática e inadimplência

A renovação contratual e a situação financeira da matrícula deverão ser tratadas de forma independente.

Quando ocorrer uma renovação automática:
- Um novo período contratual será criado.
- A matrícula continuará vinculada ao mesmo aluno.
- As cobranças do novo período serão geradas conforme as condições financeiras registradas.
- A ausência de pagamento não deverá desfazer automaticamente a renovação contratual.

Caso uma cobrança permaneça em aberto após o vencimento:
- A situação financeira da matrícula deverá ser identificada como inadimplente.
- As regras de bloqueio de acesso configuradas pela academia deverão ser respeitadas.
- O contrato e o histórico da renovação deverão ser preservados.

A inadimplência não deverá ser confundida com encerramento, cancelamento ou pausa da matrícula.

### 14.14 Renovação manual de matrículas encerradas

A academia poderá renovar manualmente uma matrícula que esteja com o status Encerrada.

A renovação deverá ocorrer na mesma matrícula, sem criar um novo cadastro de matrícula.

Durante o processo, será permitido:
- Selecionar um novo plano e suas modalidades.
- Definir novas datas de início e término.
- Definir os valores e as condições comerciais.
- Configurar as condições financeiras e os vencimentos.

Antes da confirmação, o sistema deverá apresentar as novas condições para conferência.

Após a confirmação:
- Um novo período contratual será criado.
- A matrícula voltará a ter vigência conforme a nova data de início.
- Os períodos anteriores permanecerão preservados.
- O histórico financeiro e contratual não poderá ser alterado.

### 14.15 Independência entre matrículas do mesmo aluno

Um aluno poderá possuir múltiplas matrículas simultâneas, e cada uma deverá funcionar de maneira independente.

Cada matrícula terá seu próprio:
- Plano e modalidades contratadas.
- Período de vigência.
- Status contratual.
- Histórico de renovações.
- Condições financeiras.
- Cobranças e pagamentos.
- Situação de inadimplência.
- Regras de bloqueio de acesso.
- Histórico de pausas, alterações e encerramentos.

Pausar, encerrar, cancelar, renovar ou bloquear uma matrícula não deverá alterar automaticamente as demais matrículas do mesmo aluno.

A situação geral do aluno deverá ser independente da situação individual de suas matrículas.