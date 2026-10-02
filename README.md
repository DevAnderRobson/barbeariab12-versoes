# Barbearia B12 · Balcão — Versões

Página de download do **programa de balcão da Barbearia B12**: um programa para Windows que organiza o dia da barbearia numa tela só. Ele mostra quem está esperando, quem está na cadeira e quem falta pagar, e também cuida da agenda, do caixa do dia e dos clientes.

Este repositório guarda **só os instaladores** de cada versão. O código-fonte fica num repositório privado.

**[⬇ Baixar a versão mais nova](https://github.com/DevAnderRobson/barbeariab12-versoes/releases/latest)**

---

## Para quem é

- **Barbearias pequenas e médias**, com um computador no balcão.
- **Atendentes sem experiência com computador:** os textos da tela são em português simples, os botões dizem por extenso o que fazem e as mensagens de erro explicam como resolver.
- **Donos** que querem saber quanto entrou, quanto saiu e quais clientes estão sumidos, sem planilha.

## O que o programa faz

| Parte | O que tem |
|---|---|
| **Balcão** | Três colunas na ordem do dia a dia: **Esperando → Cadeiras → Receber**. Coloca o cliente na espera, chama para a cadeira, junta serviços e bebidas na conta, dá desconto e recebe em dinheiro, Pix ou cartão. Na hora de receber, já dá para marcar o próximo corte. |
| **Agenda** | Horários do dia em colunas, uma por barbeiro. Calcula a duração e o total, avisa quando dois horários se chocam, remarca e desmarca com motivo. O botão **Chegou** coloca o cliente na espera do balcão. |
| **Caixa** | Abertura do dia com o troco, conferência da gaveta na hora, retirada de dinheiro (sangria) com motivo e fechamento com a conta de sobra ou falta. |
| **Painel** (só administrador) | Faturamento, despesas, resultado, ticket médio, horários de mais movimento, comissão estimada por barbeiro, serviços mais vendidos e a lista de **clientes para chamar de volta**. |
| **Clientes** (só administrador) | Ficha com frequência, gastos e histórico de cada um. Cadastra na mão ou importa uma planilha salva pelo Excel em CSV. |
| **Pessoas e acessos** | Dois tipos de acesso: **atendente** e **administrador**. As regras valem por dentro do programa, não só escondendo botões. |
| **Cópias de segurança** | Uma cópia automática dos dados por dia, ao abrir e ao fechar, e outra antes de cada atualização. Ficam guardadas as 30 mais recentes. |
| **Atualização** | O programa procura versão nova ao abrir e a cada 6 horas. Quem decide a hora de instalar é o administrador; o programa nunca se atualiza sozinho. |

## O que o programa **não** faz

Melhor saber antes de instalar:

- **Não emite nota fiscal** (NF-e, NFC-e ou NFS-e) nem cupom fiscal.
- **Não conversa com a maquininha de cartão.** O atendente registra no programa como o cliente pagou; a cobrança acontece na maquininha, do jeito de sempre.
- **Não tem agendamento on-line.** O cliente não marca horário por site nem por aplicativo; a agenda é usada no balcão.
- **Não envia mensagens** (WhatsApp, SMS ou e-mail) para os clientes.
- **Não sincroniza entre computadores.** Cada computador guarda os próprios dados. Dois computadores não enxergam a mesma fila.
- **Não guarda nada na nuvem.** Os dados ficam só no computador. Para ter uma cópia fora dele, copie a pasta de cópias para um pendrive ou para o Google Drive/OneDrive (veja [Seus dados](#seus-dados)).
- **Não calcula folha de pagamento.** A comissão do Painel é uma estimativa para conferência, não um fechamento de folha.
- **Não roda em Mac, Linux, celular ou tablet.** Só há instalador para Windows.

## Como instalar

**Precisa de:** Windows 10 ou 11 (64 bits). Não é preciso instalar Java nem mais nada: o instalador já traz tudo.

1. Abra a [versão mais nova](https://github.com/DevAnderRobson/barbeariab12-versoes/releases/latest) e baixe o arquivo **`.msi`** em *Assets*.
2. Dê dois cliques no arquivo baixado. O programa é instalado na pasta do usuário do Windows, **sem pedir a senha de administrador do computador**, e cria atalhos na área de trabalho e no menu Iniciar.
3. Na primeira vez que o programa abre, aparece a tela de **Primeiro acesso**. Nela, a barbearia escolhe o próprio nome e cria o usuário administrador. Depois, um guia mostra o programa passo a passo. Esse guia pode ser aberto de novo pelo botão **? Ajuda**.

> **Apareceu "O Windows protegeu o computador"?** O aviso aparece porque o instalador ainda não tem assinatura digital (um certificado pago). Clique em **Mais informações** e depois em **Executar assim mesmo**. Se quiser ter certeza de que o arquivo é o original, faça a conferência abaixo.

### Conferir se o arquivo é o original (opcional)

Cada versão traz um arquivo **`SHA256.txt`** com a "impressão digital" do instalador. No PowerShell, dentro da pasta onde o `.msi` foi baixado:

```powershell
Get-FileHash .\BarbeariaB12-1.0.0.msi -Algorithm SHA256
```

O código que aparecer precisa ser igual ao do `SHA256.txt`. Troque `1.0.0` pelo número da versão baixada. A atualização feita pelo próprio programa faz essa conferência sozinha e apaga o arquivo se ele vier diferente.

## Como atualizar

Não é preciso voltar a esta página. Quando sai uma versão nova, o programa avisa o administrador. Ele clica em **Atualizar agora** quando for melhor (de preferência no fim do dia), e o programa:

1. baixa a versão nova e confere se chegou inteira;
2. faz uma cópia de segurança dos dados;
3. fecha, instala por cima e abre de novo, mostrando **o que mudou**.

Os dados continuam onde estavam. Também dá para atualizar à mão: basta baixar o `.msi` novo e instalar por cima do antigo.

As versões usam números do tipo `1.2.3`:

- o **último** número sobe nas correções;
- o **do meio** sobe quando tem coisa nova;
- o **primeiro** sobe nas mudanças grandes.

O programa só oferece versões mais novas que a instalada.

## Seus dados

Tudo fica no próprio computador, numa pasta só:

```
%APPDATA%\BarbeariaB12\
├── database.db   (os dados do programa)
└── copias\       (as cópias de segurança)
```

- O programa **funciona sem internet**. A internet só é usada para procurar e baixar versão nova, e só neste repositório público.
- **Nenhum dado da barbearia sai do computador.** Clientes, atendimentos e valores não são enviados a lugar nenhum.
- **As senhas não ficam guardadas.** O programa guarda só um código derivado delas (PBKDF2), e por esse código não dá para descobrir a senha.
- **Desinstalar o programa não apaga os dados.**
- **Dica:** copie a pasta `copias` de vez em quando para um pendrive ou para a nuvem. Se o disco do computador quebrar, os dados estarão salvos.

## Stack

| Camada | Tecnologia |
|---|---|
| Linguagem | Kotlin 2.0 na JVM 21 |
| Telas | Swing, com tema claro e escuro |
| Banco de dados | SQLite local (driver `sqlite-jdbc`), acessado por JDBC sem ORM. As mudanças no banco são feitas por migrações versionadas. |
| Segurança | Senhas com PBKDF2-HMAC-SHA256. Permissões conferidas em cada função do sistema. |
| Cópias de segurança | `VACUUM INTO` do SQLite: uma cópia consistente mesmo com o programa aberto |
| Build | Gradle, com testes automatizados do backend |
| Instalador | `jpackage` + WiX 3 gerando um `.msi` com o Java embutido, instalado por usuário e atualizado por cima |
| Publicação | GitHub Actions: uma tag `vX.Y.Z` no repositório do código roda os testes, gera o instalador e o `SHA256.txt` e publica uma Release aqui |
| Atualização | O programa lê a API pública de Releases deste repositório, baixa o `.msi` e confere o SHA-256 antes de instalar |

O programa foi feito para rodar bem em computadores simples: usa pouca memória e quase não tem dependências.

## Sobre este repositório

- **Não tem código-fonte aqui.** Ele existe para deixar os instaladores públicos, para o programa e as barbearias baixarem sem senha. O código fica num repositório privado.
- **Cada versão é publicada automaticamente** a partir do repositório do código, depois de passar pelos testes. Ninguém sobe um instalador montado à mão.
- **As novidades** de cada versão estão em [Releases](https://github.com/DevAnderRobson/barbeariab12-versoes/releases), escritas para quem usa o programa.
- **Dúvidas ou problemas:** fale com quem instalou o programa na sua barbearia.
