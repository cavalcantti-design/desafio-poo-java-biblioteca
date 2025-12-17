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
##// Classe base
abstract class Livro {
    private String titulo;
    private String autor;
    private String isbn;
    private boolean disponivel;

    public Livro(String titulo, String autor, String isbn) {
        this.titulo = titulo;
        this.autor = autor;
        this.isbn = isbn;
        this.disponivel = true; // Livro está disponível inicialmente
    }

    public boolean isDisponivel() {
        return disponivel;
    }

    public void emprestar() {
        if (disponivel) {
            disponivel = false;
            System.out.println("Livro emprestado com sucesso!");
        } else {
            System.out.println("Este livro não está disponível.");
        }
    }

    public void devolver() {
        disponivel = true;
        System.out.println("Livro devolvido com sucesso!");
    }

    // Método que será sobrescrito nas subclasses
    public abstract void exibirDetalhes();
}

// Subclasse LivroFisico
class LivroFisico extends Livro {
    private String localizacao;

    public LivroFisico(String titulo, String autor, String isbn, String localizacao) {
        super(titulo, autor, isbn);
        this.localizacao = localizacao;
    }

    @Override
    public void exibirDetalhes() {
        System.out.println("Livro Físico - Título: " + super.titulo + ", Autor: " + super.autor + ", ISBN: " + super.isbn + ", Localização: " + localizacao);
    }
}

// Subclasse LivroDigital
class LivroDigital extends Livro {
    private String linkDownload;

    public LivroDigital(String titulo, String autor, String isbn, String linkDownload) {
        super(titulo, autor, isbn);
        this.linkDownload = linkDownload;
    }

    @Override
    public void exibirDetalhes() {
        System.out.println("Livro Digital - Título: " + super.titulo + ", Autor: " + super.autor + ", ISBN: " + super.isbn + ", Link de Download: " + linkDownload);
    }
}

// Classe Membro
class Membro {
    private String nome;
    private String cpf;
    private String email;
    private List<Livro> livrosEmprestados;

    public Membro(String nome, String cpf, String email) {
        this.nome = nome;
        this.cpf = cpf;
        this.email = email;
        this.livrosEmprestados = new ArrayList<>();
    }

    public void emprestarLivro(Livro livro) {
        if (livro.isDisponivel()) {
            livro.emprestar();
            livrosEmprestados.add(livro);
        }
    }

    public void devolverLivro(Livro livro) {
        livro.devolver();
        livrosEmprestados.remove(livro);
    }

    public void exibirLivrosEmprestados() {
        System.out.println("Livros emprestados por " + nome + ":");
        for (Livro livro : livrosEmprestados) {
            livro.exibirDetalhes();
        }
    }
}

// Classe Biblioteca
class Biblioteca {
    private List<Livro> livros;
    private List<Membro> membros;

    public Biblioteca() {
        livros = new ArrayList<>();
        membros = new ArrayList<>();
    }

    public void adicionarLivro(Livro livro) {
        livros.add(livro);
    }

    public void registrarMembro(Membro membro) {
        membros.add(membro);
    }

    public void listarLivros() {
        System.out.println("Livros na biblioteca:");
        for (Livro livro : livros) {
            livro.exibirDetalhes();
        }
    }

    public void listarLivrosDisponiveis() {
        System.out.println("Livros disponíveis para empréstimo:");
        for (Livro livro : livros) {
            if (livro.isDisponivel()) {
                livro.exibirDetalhes();
            }
        }
    }
}

Desafio desenvolvido para fins educacionais, com foco em Programação Orientada a Objetos em Java.
