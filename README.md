# Projeto Veículos — Prova de Java POO

## Instruções

Você receberá dois arquivos prontos: `TipoCombustivel.java` e `Veiculo.java`. Não é necessário alterá-los, apenas lê-los com atenção antes de começar — eles mostram exatamente o que a classe base oferece para você trabalhar.

Sua tarefa é implementar os três arquivos indicados abaixo, seguindo os comentários deixados em cada um como guia.

---

> ## ATENÇÃO — LEIA ANTES DE COMEÇAR
>
> Crie um arquivo `README.md` na raiz do projeto e coloque **no topo** o **nome completo** de cada integrante do grupo (mínimo 1, máximo 3 alunos).
>
> **Entregas sem identificação não serão corrigidas e receberão nota zero**, sem exceção. Alegar após a aplicação da prova que trabalhou em grupo ou que esqueceu de incluir o nome não será aceito como justificativa.

---

**Conceitos avaliados:**

- Herança
- Sobrescrita de métodos (override)
- Sobrecarga de métodos (overload)
- Classes abstratas
- Enums

---

## Estrutura do Projeto

```text
app/
  Main.java              (você implementa)
enums/
  TipoCombustivel.java   (fornecido)
  CategoriaVeiculo.java  (você implementa)
model/
  Veiculo.java           (fornecido)
  Carro.java             (você implementa)
```

---

## Arquivos Fornecidos

### `enums/TipoCombustivel.java`

```java
package enums;

public enum TipoCombustivel {
    GASOLINA,
    DIESEL,
    ELETRICO,
    ETANOL
}
```

---

### `model/Veiculo.java`

```java
package model;

import enums.TipoCombustivel;
import enums.CategoriaVeiculo;

public abstract class Veiculo {

    private String marca;
    private String modelo;
    private int ano;
    private int velocidadeMaxima;
    private TipoCombustivel tipoCombustivel;
    private CategoriaVeiculo categoria;

    public Veiculo(String marca, String modelo, int ano,
                   int velocidadeMaxima, TipoCombustivel tipoCombustivel,
                   CategoriaVeiculo categoria) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
        this.velocidadeMaxima = velocidadeMaxima;
        this.tipoCombustivel = tipoCombustivel;
        this.categoria = categoria;
    }

    public abstract void ligarMotor();

    public void buzinar() {
        System.out.println(marca + " " + modelo + " buzina: Beep!");
    }

    public void acelerar(int velocidade) {
        System.out.println(marca + " " + modelo + " acelera para " + velocidade + " km/h");
    }

    public void exibirInfo() {
        System.out.println("Marca: " + marca);
        System.out.println("Modelo: " + modelo);
        System.out.println("Ano: " + ano);
        System.out.println("Velocidade máxima: " + velocidadeMaxima + " km/h");
        System.out.println("Combustível: " + tipoCombustivel.name());
        System.out.println("Categoria: " + categoria.getNomeExibicao());
    }

    public String getMarca() { return marca; }
    public String getModelo() { return modelo; }
    public int getAno() { return ano; }
    public int getVelocidadeMaxima() { return velocidadeMaxima; }
    public TipoCombustivel getTipoCombustivel() { return tipoCombustivel; }
    public CategoriaVeiculo getCategoria() { return categoria; }
}
```

---

## Arquivos para Implementar

### `enums/CategoriaVeiculo.java`

Este enum segue a mesma ideia do `TipoCombustivel`, mas com um pouco mais de estrutura: cada constante carrega um código numérico e um nome para exibição.

```java
package enums;

public enum CategoriaVeiculo {

    /*
     * Defina as seguintes constantes, cada uma com um codigo (int) e um nomeExibicao (String):
     *
     *   PASSEIO     → codigo 1, exibicao "Passeio"
     *   ESPORTIVO   → codigo 2, exibicao "Esportivo"
     *   UTILITARIO  → codigo 3, exibicao "Utilitário"
     */

    // private final int codigo
    // private final String nomeExibicao

    // Construtor CategoriaVeiculo(int codigo, String nomeExibicao)

    // getNomeExibicao()

}
```

---

### `model/Carro.java`

A classe `Carro` estende `Veiculo`. Boa parte do comportamento já vem pronta da classe pai — sua tarefa é especializar onde necessário e acrescentar o que é específico de um carro.

```java
package model;

import enums.TipoCombustivel;
import enums.CategoriaVeiculo;

public class Carro extends Veiculo {

    // Atributos adicionais:
    //   int numeroDePortas
    //   String tipoTransmissao   ("Manual" ou "Automatico")

    // Construtor:
    //   Chame super() com todos os atributos de Veiculo.
    //   Em seguida, inicialize os atributos específicos do Carro.

    // SOBRESCRITA: ligarMotor()
    //   Imprimir: "[marca] [modelo] motor liga: Vrum!"

    // SOBRESCRITA: buzinar()
    //   Imprimir: "[marca] [modelo] buzina: Bi bi!"

    // Herdado sem alteração: acelerar(int velocidade)

    // SOBRECARGA: acelerar(int velocidade, String marcha)
    //   Imprimir: "[marca] [modelo] acelera para [velocidade] km/h na marcha [marcha]"

    // SOBRESCRITA: exibirInfo()
    //   Chame super.exibirInfo() para aproveitar o que já existe,
    //   depois imprima os campos específicos do Carro.

    // Getters para os atributos específicos do Carro.

}
```

---

### `app/Main.java`

No Main, o objetivo é demonstrar na prática o que foi implementado. Instancie dois carros com características diferentes, exercite os métodos e compare o comportamento entre eles.

```java
package app;

public class Main {

    public static void main(String[] args) {

        // 1. Crie um objeto Carro com valores à sua escolha.

        // 2. Chame os métodos: ligarMotor(), buzinar(),
        //    acelerar(int), acelerar(int, String), exibirInfo()

        // 3. Crie um segundo Carro com valores diferentes do primeiro
        //    (marca, modelo, transmissão e número de portas diferentes).
        //    Chame exibirInfo() nos dois e depois compare a velocidade máxima
        //    de cada um usando getVelocidadeMaxima(), imprimindo qual dos dois é mais rápido.

    }

}
```

---

## Saída Esperada no Console

```text
Toyota Corolla motor liga: Vrum!
Toyota Corolla buzina: Bi bi!
Toyota Corolla acelera para 80 km/h
Toyota Corolla acelera para 100 km/h na marcha 3ª
Marca: Toyota
Modelo: Corolla
Ano: 2022
Velocidade máxima: 180 km/h
Combustível: GASOLINA
Categoria: Passeio
Número de portas: 4
Transmissão: Automatico
---
Marca: Honda
Modelo: Civic
Ano: 2020
Velocidade máxima: 210 km/h
Combustível: ETANOL
Categoria: Esportivo
Número de portas: 2
Transmissão: Manual
---
Honda Civic é mais rápido.
```

## Critérios de Avaliação

| Item | Pontuação |
| --- | --- |
| Enum `CategoriaVeiculo` com as 3 constantes, atributos, construtor e `getNomeExibicao()` | 25 |
| `Carro` estende `Veiculo` com construtor correto usando `super()` | 20 |
| `Carro` sobrescreve `ligarMotor()` e `buzinar()` corretamente | 20 |
| `Carro` sobrecarrega `acelerar(int, String)` corretamente | 15 |
| `Carro` sobrescreve `exibirInfo()` chamando `super.exibirInfo()` | 10 |
| `Main` instancia dois carros, chama todos os métodos e compara a velocidade máxima entre eles | 10 |
| **Total** | **100** |

---

## Compilar e Executar

```bash
javac app/Main.java model/*.java enums/*.java
java app.Main
```

---

Boa sorte!
