# desafio-poo-java-biblioteca
Você vai criar um sistema de gerenciamento de biblioteca, onde é possível registrar, emprestar, devolver e listar livros. O sistema deve ser capaz de lidar com diferentes tipos de livros, como livros físicos e livros digitais. Além disso, o sistema precisa controlar quem são os membros da biblioteca e o histórico de empréstimos de livros.
Desafio em Java para praticar Programação Orientada a Objetos (POO) com abstração, encapsulamento, herança e polimorfismo.
.gitignore
LICENSE
src/biblioteca/Main.java
- Classe abstrata `Livro` define atributos e comportamentos comuns.
- Atributos privados com acesso via getters e métodos controlados.
- `LivroFisico` e `LivroDigital` herdam de `Livro`.
- Método `exibirDetalhes()` sobrescrito em cada tipo de livro.
- --
- Cadastro de livros físicos e digitais
- Registro de membros
- Empréstimo e devolução de livros
- Listagem de livros disponíveis
- Histórico de empréstimos por membro
--
1. Clone o repositório
2. Abra em uma IDE Java (IntelliJ, Eclipse ou VS Code)
3. Execute a classe `Main`

- Menu interativo no console
- Persistência de dados em arquivos
- Limite de empréstimos por membro
- Relatórios de livros mais emprestados
##
Desafio desenvolvido para fins educacionais, com foco em Programação Orientada a Objetos em Java.
