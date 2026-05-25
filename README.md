# Projeto Robôs — Prova de Java POO

## Instruções

Você receberá dois arquivos prontos: `TipoEnergia.java` e `Robo.java`. Não é necessário alterá-los, apenas lê-los com atenção antes de começar — eles mostram exatamente o que a classe base oferece para você trabalhar.

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
  TipoEnergia.java       (fornecido)
  CategoriaRobo.java     (você implementa)
model/
  Robo.java              (fornecido)
  RoboAndroide.java      (você implementa)
```

---

## Arquivos Fornecidos

### `enums/TipoEnergia.java`

```java
package enums;

public enum TipoEnergia {
    SOLAR,
    BATERIA,
    ELETRICO,
    NUCLEAR
}
```

---

### `model/Robo.java`

```java
package model;

import enums.TipoEnergia;
import enums.CategoriaRobo;

public abstract class Robo {

    private String fabricante;
    private String modelo;
    private int ano;
    private int velocidadeMaxima;
    private TipoEnergia tipoEnergia;
    private CategoriaRobo categoria;

    public Robo(String fabricante, String modelo, int ano,
                int velocidadeMaxima, TipoEnergia tipoEnergia,
                CategoriaRobo categoria) {
        this.fabricante = fabricante;
        this.modelo = modelo;
        this.ano = ano;
        this.velocidadeMaxima = velocidadeMaxima;
        this.tipoEnergia = tipoEnergia;
        this.categoria = categoria;
    }

    public abstract void iniciar();

    public void emitirSom() {
        System.out.println(fabricante + " " + modelo + " emite: Bip!");
    }

    public void mover(int velocidade) {
        System.out.println(fabricante + " " + modelo + " se move a " + velocidade + " km/h");
    }

    public void exibirInfo() {
        System.out.println("Fabricante: " + fabricante);
        System.out.println("Modelo: " + modelo);
        System.out.println("Ano: " + ano);
        System.out.println("Velocidade máxima: " + velocidadeMaxima + " km/h");
        System.out.println("Energia: " + tipoEnergia.name());
        System.out.println("Categoria: " + categoria.getNomeExibicao());
    }

    public String getFabricante() { return fabricante; }
    public String getModelo() { return modelo; }
    public int getAno() { return ano; }
    public int getVelocidadeMaxima() { return velocidadeMaxima; }
    public TipoEnergia getTipoEnergia() { return tipoEnergia; }
    public CategoriaRobo getCategoria() { return categoria; }
}
```

---

## Arquivos para Implementar

### `enums/CategoriaRobo.java`

Este enum segue a mesma ideia do `TipoEnergia`, mas com um pouco mais de estrutura: cada constante carrega um código numérico e um nome para exibição.

```java
package enums;

public enum CategoriaRobo {

    /*
     * Defina as seguintes constantes, cada uma com um codigo (int) e um nomeExibicao (String):
     *
     *   INDUSTRIAL  → codigo 1, exibicao "Industrial"
     *   DOMESTICO   → codigo 2, exibicao "Doméstico"
     *   MILITAR     → codigo 3, exibicao "Militar"
     */

    // private final int codigo
    // private final String nomeExibicao

    // Construtor CategoriaRobo(int codigo, String nomeExibicao)

    // getNomeExibicao()

}
```

---

### `model/RoboAndroide.java`

A classe `RoboAndroide` estende `Robo`. Boa parte do comportamento já vem pronta da classe pai — sua tarefa é especializar onde necessário e acrescentar o que é específico de um robô androide.

```java
package model;

import enums.TipoEnergia;
import enums.CategoriaRobo;

public class RoboAndroide extends Robo {

    // Atributos adicionais:
    //   int numeroBracos
    //   String tipoProcessador   (ex: "ARM" ou "x86")

    // Construtor:
    //   Chame super() com todos os atributos de Robo.
    //   Em seguida, inicialize os atributos específicos do RoboAndroide.

    // SOBRESCRITA: iniciar()
    //   Imprimir: "[fabricante] [modelo] inicializa: Beep boop!"

    // SOBRESCRITA: emitirSom()
    //   Imprimir: "[fabricante] [modelo] emite: Zzt zzt!"

    // Herdado sem alteração: mover(int velocidade)

    // SOBRECARGA: mover(int velocidade, String direcao)
    //   Imprimir: "[fabricante] [modelo] se move a [velocidade] km/h em direção a [direcao]"

    // SOBRESCRITA: exibirInfo()
    //   Chame super.exibirInfo() para aproveitar o que já existe,
    //   depois imprima os campos específicos do RoboAndroide.

    // Getters para os atributos específicos do RoboAndroide.

}
```

---

### `app/Main.java`

No Main, o objetivo é demonstrar na prática o que foi implementado. Instancie dois robôs com características diferentes, exercite os métodos e compare o comportamento entre eles.

```java
package app;

public class Main {

    public static void main(String[] args) {

        // 1. Crie um objeto RoboAndroide com valores à sua escolha.

        // 2. Chame os métodos: iniciar(), emitirSom(),
        //    mover(int), mover(int, String), exibirInfo()

        // 3. Crie um segundo RoboAndroide com valores diferentes do primeiro
        //    (fabricante, modelo, processador e número de braços diferentes).
        //    Chame exibirInfo() nos dois e depois compare a velocidade máxima
        //    de cada um usando getVelocidadeMaxima(), imprimindo qual dos dois é mais rápido.

    }

}
```

---

## Saída Esperada no Console

```text
RoboTech Atlas-1 inicializa: Beep boop!
RoboTech Atlas-1 emite: Zzt zzt!
RoboTech Atlas-1 se move a 40 km/h
RoboTech Atlas-1 se move a 60 km/h em direção a Norte
Fabricante: RoboTech
Modelo: Atlas-1
Ano: 2023
Velocidade máxima: 80 km/h
Energia: BATERIA
Categoria: Industrial
Número de braços: 2
Processador: ARM
---
Fabricante: NeoCorp
Modelo: Nexus-7
Ano: 2024
Velocidade máxima: 120 km/h
Energia: SOLAR
Categoria: Militar
Número de braços: 4
Processador: x86
---
NeoCorp Nexus-7 é mais rápido.
```

## Critérios de Avaliação

| Item | Pontuação |
| --- | --- |
| Enum `CategoriaRobo` com as 3 constantes, atributos, construtor e `getNomeExibicao()` | 25 |
| `RoboAndroide` estende `Robo` com construtor correto usando `super()` | 20 |
| `RoboAndroide` sobrescreve `iniciar()` e `emitirSom()` corretamente | 20 |
| `RoboAndroide` sobrecarrega `mover(int, String)` corretamente | 15 |
| `RoboAndroide` sobrescreve `exibirInfo()` chamando `super.exibirInfo()` | 10 |
| `Main` instancia dois robôs, chama todos os métodos e compara a velocidade máxima entre eles | 10 |
| **Total** | **100** |

---

## Compilar e Executar

```bash
javac app/Main.java model/*.java enums/*.java
java app.Main
```

---

Boa sorte!

---

Ao final da aula com 5 minutos faltantes começaremos a recolher as pastas salvas na area de trabalho com o pendrive, por favor lembre-se de salvar os codigos e deixar a pasta encontravel na area de trabalho.
