## Árvores

Árvores são estruturas de dados especiais, que tem certa semelhança com as listas-ligadas.

Se nas listas-ligadas cada nó se ligava ao próximo, sempre 1 -> 1, nas árvores cada nó pode ligar 1 -> N.

Ou seja, **a partir de um dado nó podem sair N ligações para novos nós.**

Também é importante destacar que **cada nó é uma árvore**, portanto, **árvores são estruturas recursivas**.

Ser recursiva significa que **todas as regras que se aplicam às árvores também se aplicam ao nós**.

Assim, dizemos que **cada nó é a raiz de uma sub-árvore**.

Por falar em raiz, **cada árvore parte de um único nó chamado raiz**.

Vamos definir uma árvore formalmente:

1. Árvores, assim como as demais estruturas que vimos, deve ter um **tipo**, que chamamos de *T*.
2. Uma árvore pode ser vazia.
3. Uma árvore pode conter um elemento, apenas a raiz, do tipo T.
4. Uma árvore pode conter um finito número de sub-árvores do tipo T, associado à raiz;

Se a ordem dos elementos de uma árvore for relevante chamamos de **Árvore Ordenada**.

Temos nomenclaturas especiais para os nós de acordo com a posição deles e o nível deles na árvore:

#### Propriedades de um nó

Nível é um valor inteiro que começa em **1 para a raiz** e **aumenta em 1 a cada camada da árvore abaixo da raiz**.

**Um nó B abaixo de um nó A é chamado de filho de A. A é chamado de pai de B. Um nó Pai tem nível 1 menor que um nó filho**.

**Um nó C também filho de A é chamado de irmão de B. Irmãos têm mesmo nível**.

**Um nó com dois filhos tem grau 2. Em outras palavras, chamamos de grau a quantidade de filhos de um nó**.

**Um nó sem filhos é chamado de folha. Ou de nó terminal.**

**Um nó que não é folha é chamado de não-terminal ou nó interno.**

#### Propriedades de uma árvore

**Altura (profundidade) de um árvore é o maior nível que contenha nós.**

**Grau de uma árvore é igual ao grau do nó que tiver mais filhos.**

#### Implementação

A estrutura de uma árvore é muito simples de representar em JAVA.

Uma árvore será composta de um valor (raiz) e um vetor de Arvore:

```java
public class Arvore{
	
  public int valor;
  
  public Arvore[] filhos;
  
}
```

Para facilitar a criação da árvore vamos adicionar um construtor:

```java
public class Arvore{
	
    public int valor;

    public Arvore[] filhos;

    public Arvore(int valor, Arvore[] filhos){
        this.valor = valor;
        this.filhos = filhos;
    }
}
```

E um método para imprimir:

```java
public class Arvore{
	
  private int valor;
  
  private Arvore[] filhos;
  
  public Arvore(int valor, Arvore[] filhos){
    this.valor = valor;
    this.filhos = filhos;
  }
  
  public void print(){
  	
    System.out.print(" " + this.valor);
    
    if(this.filhos != null){
      for(Arvore filho : this.filhos){
        filho.print();
      }
    }
  }
}
```

Para testar a árvore podemos usar o seguinte código

```java
public class Programa
{
  public static void main(String[] args)
  {
    Arvore arvore = new Arvore(
      1, 
      new Arvore[]{
        new Arvore(2, new Arvore[]{
        	new Arvore(4,null),
          	new Arvore(5,null)
        }), 
        new Arvore(3, new Arvore[]{ 
        	new Arvore(6, null),
          	new Arvore(7, null)
        })});
    arvore.print();
  }
}
```