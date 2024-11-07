# post-it_share
O Post-it Share é uma aplicação de notas rápidas que permite aos usuários criarem, compartilharem e visualizarem anotações efêmeras. As notas compartilhadas ficam disponíveis por um curto período de tempo e são automaticamente removidas, promovendo uma maneira rápida e temporária de compartilhar informações.

## Funcionalidades
- Criação de Notas: Insira texto diretamente na área de edição e clique em "Compartilhar" para gerar um link de compartilhamento.
- Compartilhamento por Link: Um link exclusivo é gerado para cada nota, permitindo que outros usuários visualizem o conteúdo.
- Notas Temporárias: As notas são excluídas automaticamente após serem visualizadas ou expiram após sete dias sem serem abertas.
- Banco de Dados: As notas são salvas em um banco SQLite e gerenciadas para garantir a exclusão de conteúdo expirado.


## Tecnologias Utilizadas
- Frontend: HTML5, CSS3, JavaScript e HTMX para interações assíncronas.
- Backend: Node.js com Express.js para o servidor.
- Banco de Dados: SQLite para armazenamento de notas.
- UUID: Cada nota recebe um identificador exclusivo para o link de compartilhamento.


## Estrutura do Projeto
- HTML e CSS: Interface simples, com um design de "sticky note" (nota adesiva).
- JavaScript (Frontend): Manipula as interações e utiliza HTMX para envio assíncrono de dados ao backend.
- Backend (Node.js e Express): Recebe e processa as notas, gerencia os links de compartilhamento e exclui notas expiradas.
- Banco de Dados (SQLite): Armazena as notas com data de criação e abertura, permitindo gerenciar a validade das notas.


## Configuração do Projeto
***Pré-requisitos***
- Node.js (versão 14 ou superior)
- NPM (gerenciador de pacotes do Node.js)
***Passo a Passo***
1. Clone o repositório:
    ```bash
    git clone https://github.com/seu-usuario/post-it-share.git
    cd post-it-share
2. Instale as dependências:
    ```bash
    npm install
3. Inicie o servidor:
    ```bash
    npm start
4. Abra o navegador e acesse `http://localhost:3000` para usar a aplicação.

## Estrutura de Código
***Backend***
- `app.js`: Configuração do servidor e rotas.
- Rota `/notes`: Recebe o conteúdo da nota e retorna um link de compartilhamento.
- Rota `/share/:id`: Exibe a nota com base no ID, e marca a nota como "aberta".
- Banco de Dados: Realiza a limpeza de notas expiradas (não visualizadas após 7 dias ou já visualizadas há mais de 5 minutos).
***Banco de Dados***
- `db.js`: Configura e gerencia a conexão SQLite.
- `saveNote(id, content)`: Salva uma nova nota com o conteúdo fornecido.
- `getNote(id)`: Obtém a nota usando o ID.
- `markNoteAsOpened(id)`: Marca a nota como visualizada.
- `deleteExpiredNotes()`: Exclui notas expiradas.

## Exemplo de Uso
1. Acesse a aplicação e insira uma anotação na área de texto.
2. Clique em Compartilhar para gerar um link exclusivo.
3. Envie o link para qualquer pessoa que deseja acessar a nota.
4. Após ser visualizada, a nota expira em cinco minutos.

## Dependências
- `express`: Para configurar o servidor.
- `sqlite3`: Para manipulação e armazenamento de dados localmente.
