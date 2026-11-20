# Validação defensiva em máquina virtual

Copie o projeto para uma VM de testes autorizada onde o Codex ou o Hermes esteja disponível. Abra o agente na raiz do projeto. Os arquivos INI são fictícios e podem ser analisados sem iniciar serviços.

## Caso com falha conhecida

Peça ao agente para usar a habilidade de triagem defensiva, ler somente o arquivo config-before.ini desta pasta e relatar problemas sustentados pelo arquivo. Peça componente, evidência, prioridade, confiança, correção e verificação.

O agente deve identificar a identidade administrativa compartilhada pelas duas seções e recomendar uma identidade própria por serviço, com privilégios mínimos. O arquivo sustenta o achado de configuração. O alcance real da conta e a necessidade dos privilégios dependem de evidências adicionais.

## Caso corrigido

Abra uma nova sessão na mesma pasta. Faça o mesmo pedido usando somente config-after.ini. O agente deve reconhecer as identidades distintas e os papéis específicos declarados. A configuração por si só não comprova que a aplicação aplica esses papéis. O agente não deve repetir o achado de conta administrativa compartilhada.

## Critério de aprovação

Guarde a saída dos dois testes e confira se o agente cita a evidência, propõe uma correção pertinente e deixa de apontar o mesmo problema na configuração corrigida. A validação do agente fica pendente até obter as duas respostas na VM.

## Resultado no Codex

Em 20/11/2026, o Codex CLI leu a habilidade e comparou os dois arquivos em modo somente leitura. Identificou a conta administrativa compartilhada na configuração inicial e reconheceu as contas distintas e os papéis específicos na corrigida. Recomendou conferir as permissões efetivas e o funcionamento dos serviços.

O teste comparativo passou no Windows. A validação na máquina virtual e a verificação das permissões efetivas estão pendentes.