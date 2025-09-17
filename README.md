## 1. Meus comentários sobre o primeiro trecho do livro Software Engineering at Google:

  O texto explica que programação e engenharia de software não são exatamente a mesma coisa. Programação está mais ligada a escrever código, enquanto engenharia de software envolve aplicar conhecimentos teóricos e métodos estruturados para criar sistemas mais precisos e confiáveis, de forma semelhante ao trabalho de engenheiros de outras áreas.

Em profissões como engenharia civil ou mecânica, há normas e práticas muito rigorosas para evitar erros graves. Na programação, historicamente, essas regras não eram tão seguidas, mas, com a presença crescente do software no cotidiano, torna-se necessário adotar métodos mais rigorosos. O Google, com sua experiência, busca apresentar formas de tornar o desenvolvimento de software mais confiável.



## 2. Meu comentário sobre o segundo trecho:

  Esse segundo trecho apresenta a ideia de que engenharia de software não é apenas escrever código, mas também incluir todas as ferramentas e processos que ajudam a criar e manter esse código ao longo do tempo. A questão central é como manter o código útil e sustentável durante toda a sua vida, desde a criação até a desativação.

A visão do Google, baseada em sua experiência, é que engenharia de software pode ser vista como “programação integrada ao longo do tempo”, ou seja, levando em conta as mudanças e a manutenção contínua. O livro destaca três princípios fundamentais que devem guiar a forma como o código é projetado e escrito:

1. Tempo e Mudança – como o código precisa se adaptar durante sua vida útil;

2. Escala e Crescimento – como a organização deve se ajustar à medida que evolui;

3. Compensações e Custos – como tomar decisões considerando as lições dos dois pontos anteriores.



## 3. Exemplos de tradeoffs:

`1. Desempenho vs. Legibilidade do Código:`

Exemplo: Ao otimizar um trecho de código para melhorar o desempenho (por exemplo, usando técnicas como cache ou algoritmos mais complexos), o código pode se tornar mais difícil de ler e manter.

Tradeoff: Em um projeto de software, há uma escolha entre otimizar o código para ser mais rápido e eficiente ou mantê-lo simples e fácil de entender para os desenvolvedores, facilitando a manutenção e a evolução do sistema.

`2. Escalabilidade vs. Complexidade Arquitetural:`

Exemplo: Ao projetar um sistema que precisa lidar com um grande volume de tráfego, você pode optar por uma arquitetura distribuída que permita escalabilidade horizontal (como microserviços). No entanto, essa abordagem tende a aumentar a complexidade do sistema, pois requer gestão de vários serviços, comunicação entre eles e controle de falhas.

Tradeoff: A busca por escalabilidade pode resultar em um sistema mais complexo, que exige mais esforço para desenvolvimento, monitoramento e manutenção.

`3. Desenvolvimento Rápido vs. Qualidade do Código:`

Exemplo: Em um cenário de desenvolvimento ágil, pode-se priorizar a entrega rápida de funcionalidades, o que pode resultar em código com menos cobertura de testes, maior dívida técnica ou maior acoplamento entre componentes.

Tradeoff: Sacrificar a qualidade do código para entregar funcionalidades rapidamente pode acelerar o desenvolvimento inicial, mas a longo prazo pode resultar em um sistema mais difícil de manter e propenso a falhas.

## 4. Diagrama de Classes UML (Padaria):
<img width="647" height="429" alt="Padaria" src="https://github.com/user-attachments/assets/8666184d-b801-47d3-9768-fb875c75c678" />

## 5. Código Java de cada uma das classes (Padaria): 

`Pão:`
```
public class Pao {
    private float preco;
    private float vendasPao;
    
    public Pao(float preco) {
        this.preco = preco;
        this.vendasPao = 0;
    }
    
    public float getPreco() {
        return preco;
    }
    public void setPreco(float preco) {
        this.preco = preco;
    }
    public float getVendasPao() {
        return vendasPao;
    }
    public void venderPao() {
        this.vendasPao++;
    }
}

```

`Padaria:`
```
public class Padaria {
    private boolean temPao;
    private String horarioFuncionamento;

    public Padaria(boolean temPao, String horarioFuncionamento) {
        this.temPao = temPao;
        this.horarioFuncionamento = horarioFuncionamento;
    }

    public float renda() {
        return temPao ? 100.0f : 50.0f;
    }

    public boolean isTemPao() {
        return temPao;
    }
    public void setTemPao(boolean temPao) {
        this.temPao = temPao;
    }

    public String getHorarioFuncionamento() {
        return horarioFuncionamento;
    }
    public void setHorarioFuncionamento(String horarioFuncionamento) {
        this.horarioFuncionamento = horarioFuncionamento;
    }
}
``` 

`Cliente:`
```
public class Cliente {
    public String fazerPedido(Padaria padaria) {
        if (padaria.isTemPao()) {
            return "Pedido feito!";
        } else {
            return "Desculpe, o pão não está disponível.";
        }
    }

    public boolean checarRequisitos(float preco, String horarioFuncionamento, boolean temPao) {
        return preco < 5 && temPao && horarioFuncionamento.equals("Aberto");
    }
}
```
## 6. Testes automatizados:
`Teste:`
```
public class Teste {
    public static void main(String[] args) {
        Pao pao = new Pao(3.50f);
        Padaria padaria = new Padaria(true, "Aberto");

        Cliente cliente = new Cliente();

        System.out.println(cliente.fazerPedido(padaria));

        boolean podeFazerPedido = cliente.checarRequisitos(pao.getPreco(), padaria.getHorarioFuncionamento(), padaria.isTemPao());
        System.out.println("O cliente pode fazer o pedido? " + podeFazerPedido);

        pao.venderPao();
        System.out.println("Vendas de pão: " + pao.getVendasPao());
    }
}
```
## 7. Diagrama de Classes UML (Cinema):
<img width="770" height="606" alt="Cinema" src="https://github.com/user-attachments/assets/a5da012a-0645-42ff-9ae1-e73c6b6d57a1" />

## 8. Código Java de cada uma das classes (Cinema):

`Cinema`
```
package Cinema;

import java.util.ArrayList;
import java.util.List;

public class Cinema {
    private List<Filme> filmes;
    private List<Cliente> clientes;
    private List<Ingresso> ingressos;
    private int contadorIngressos;

    public Cinema() {
        this.filmes = new ArrayList<>();
        this.clientes = new ArrayList<>();
        this.ingressos = new ArrayList<>();
        this.contadorIngressos = 0;
    }

    public void adicionarFilme(Filme f) {
        filmes.add(f);
        System.out.println("Filme '" + f.getTitulo() + "' adicionado ao cinema.");
    }

    public void registrarCliente(Cliente c) {
        clientes.add(c);
        System.out.println("Cliente '" + c.getNome() + "' registrado no cinema.");
    }

    public Ingresso venderIngresso(Cliente c, Filme f) {
        if (c.getIdade() < f.getClassificacao()) {
            System.out.println("Venda negada para " + c.getNome() + ": " +
                    "idade (" + c.getIdade() + ") não atende a classificação do filme (" +
                    f.getClassificacao() + " anos).");
            return null;
        }

        contadorIngressos++;
        String codigoIngresso = "ING-" + contadorIngressos;

        double preco = f.getPrecoIngressoInteiro();
        if (c.getIdade() < 18) {
            preco /= 2;
        }

        Ingresso novoIngresso = new Ingresso(codigoIngresso, f, c, preco);
        ingressos.add(novoIngresso);

        System.out.println("Ingresso vendido com sucesso!");
        novoIngresso.exibirIngresso();
        return novoIngresso;
    }

    public void listarFilmes() {
        System.out.println("\n --- Filmes em Cartaz ---");
        for (Filme filme : filmes) {
            filme.exibirInfo();
            System.out.println("---------------------------");
        }
    }
}
```

`Ingressos`
```
package Cinema;

import java.util.ArrayList;
import java.util.List;

public class Cinema {
    private List<Filme> filmes;
    private List<Cliente> clientes;
    private List<Ingresso> ingressos;
    private int contadorIngressos;

    public Cinema() {
        this.filmes = new ArrayList<>();
        this.clientes = new ArrayList<>();
        this.ingressos = new ArrayList<>();
        this.contadorIngressos = 0;
    }

    public void adicionarFilme(Filme f) {
        filmes.add(f);
        System.out.println("Filme '" + f.getTitulo() + "' adicionado ao cinema.");
    }

    public void registrarCliente(Cliente c) {
        clientes.add(c);
        System.out.println("Cliente '" + c.getNome() + "' registrado no cinema.");
    }

    public Ingresso venderIngresso(Cliente c, Filme f) {
        if (c.getIdade() < f.getClassificacao()) {
            System.out.println("Venda negada para " + c.getNome() + ": " +
                    "idade (" + c.getIdade() + ") não atende a classificação do filme (" +
                    f.getClassificacao() + " anos).");
            return null;
        }

        contadorIngressos++;
        String codigoIngresso = "ING-" + contadorIngressos;

        double preco = f.getPrecoIngressoInteiro();
        if (c.getIdade() < 18) {
            preco /= 2;
        }

        Ingresso novoIngresso = new Ingresso(codigoIngresso, f, c, preco);
        ingressos.add(novoIngresso);

        System.out.println("Ingresso vendido com sucesso!");
        novoIngresso.exibirIngresso();
        return novoIngresso;
    }

    public void listarFilmes() {
        System.out.println("\n --- Filmes em Cartaz ---");
        for (Filme filme : filmes) {
            filme.exibirInfo();
            System.out.println("---------------------------");
        }
    }
}
```

`Cliente`
```
package Cinema;

public class Cliente {
    private String nome;
    private int idade;

    public Cliente(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    public String getNome() {
        return nome;
    }

    public int getIdade() {
        return idade;
    }

    public void comprarIngresso(Cinema cinema, Filme filme) {
        cinema.venderIngresso(this, filme);
    }
}
```
`Filme:`
```package Cinema;

public class Filme {
    private String titulo;
    private int duracao;
    private int classificacao;
    private double precoIngressoInteiro;

    public Filme(String titulo, int duracao, int classificacao, double precoIngressoInteiro) {
        this.titulo = titulo;
        this.duracao = duracao;
        this.classificacao = classificacao;
        this.precoIngressoInteiro = precoIngressoInteiro;
    }

    public String getTitulo() {
        return titulo;
    }

    public int getDuracao() {
        return duracao;
    }

    public int getClassificacao() {
        return classificacao;
    }

    public double getPrecoIngressoInteiro() {
        return precoIngressoInteiro;
    }

    public void exibirInfo() {
        System.out.println(" Título: " + titulo);
        System.out.println(" Duração: " + duracao + " min");
        System.out.println(" Classificação: " + classificacao + " anos");
        System.out.println(" Preço do Ingresso: R$" + String.format("%.2f", precoIngressoInteiro));
    }
}
```

## 9. Testes automatizados:
`Teste:`
```
package Cinema;

public class TesteCinema {
    public static void main(String[] args) {
        Cinema cinema = new Cinema();

        Filme f1 = new Filme("Matrix", 120, 16, 20.0);
        Filme f2 = new Filme("Toy Story", 90, 0, 15.0);
        Filme f3 = new Filme("O Exorcista", 110, 18, 25.0);

        cinema.adicionarFilme(f1);
        cinema.adicionarFilme(f2);
        cinema.adicionarFilme(f3);

        Cliente joao = new Cliente("João", 17);  // deve pagar meia em filmes que puder assistir
        Cliente maria = new Cliente("Maria", 12); // pode assistir só alguns filmes
        Cliente carlos = new Cliente("Carlos", 20); // paga inteira
        Cliente ana = new Cliente("Ana", 8);  // restrição maior

        cinema.registrarCliente(joao);
        cinema.registrarCliente(maria);
        cinema.registrarCliente(carlos);
        cinema.registrarCliente(ana);

        System.out.println("\n--- TESTES DE COMPRA ---");
        joao.comprarIngresso(cinema, f1);
        maria.comprarIngresso(cinema, f1);
        maria.comprarIngresso(cinema, f2);
        carlos.comprarIngresso(cinema, f1);
        ana.comprarIngresso(cinema, f3);

        cinema.listarFilmes();
    }
}
```





