## Árvores Binárias

Formalmente árvores binárias são **árvores de grau 2 ordenadas**.

Em outras palavras, **a cada nó se associam apenas 2 sub-árvores**.

Como existem apenas duas sub-árvores podemos chamá-las de **direita** e **esquerda**;

Segue abaixo a implementação básica em JAVA:

```java
public class ArvoreBinaria {
    private Integer raiz;
    private ArvoreBinaria esquerda;
    private ArvoreBinaria direita;
}
```

Para inserir um novo valor fazemos o seguinte algoritmo:

1. Se a raiz estiver vazia -> inserimos o valor na raiz.
2. Senão: Se o valor for maior que o da raiz escolhemos direita, se for menor escolhemos esquerda.
3. Se o nó escolhido estiver vazio -> inserimos o valor no nó.
4. Senão chamamos o mesmo algoritmo para a sub-árvore escolhida em 2.

```java
public void inserir(Integer no) {
        if (this.raiz == null) {
            this.raiz = no;
        } 
        else {
            if (no > this.raiz) {
                if (this.direita == null) {
                    this.direita = new ArvoreBinaria();
                }
                this.direita.inserir(no);
            } else if (no < this.raiz) {
                if (this.esquerda == null) {
                    this.esquerda = new ArvoreBinaria();
                }
                this.esquerda.inserir(no);
            }
        }
    }
```
Para imprimir uma árvore binária recursivamente podemos usar o método a seguir:

```java
public void print(){
    System.out.println(this.raiz);
    if(this.esquerda != null) esquerda.print();
    if(this.direita  != null) direita.print();
}
```
Para verificar se um número existe na árvore também podemos usar um método recursivo:

```java
public boolean contains(int valor){
    if(this.raiz == valor) return true;
    else{
        if(esquerda != null) this.esquerda.contains(valor);
        if(direita != null) this.direita.contains(valor);
    }
    return false;
}
```

#### Percorrendo uma árvore binária:

```
    A
   / \
  B   D
 /   / \
C   E   F
```

### Pré-Ordem:

Você deve visitar primeiro a raiz, depois a sub-árvore esquerda e por último a sub-árvore direita.

Resultado: `ABCDEF`

### Em-ordem (In-Ordem): 

Você deve visitar primeiro a sub-árvore esquerda, depois a raiz e por último a sub-árvore direita.

Resultado: `CBAEDF`

### Pós-Ordem:

Você deve visitar primeiro a sub-árvore esquerda, depois a sub-árvore direita e por último a raiz.

Resultado: `CBEFDA`

## Árvores AVL (Adelson Velsky e Landis):

São árvores binárias ordenadas e balanceadas.

Chamamos de balanceadas árvores em que nenhuma folha está em uma altura (ou tem nível) maior ou igual que o nível da folha mais profunda da árvore oposta + 2.

Nos exemplos abaixo não levamos em conta ordenação, apenas o balanceamento:

```
    A
   / \
  B   D
 /   / \
C   E   F
```

Nesse exemplo a árvore está balanceada, por que a árvore esquerda e direita terminam no mesmo nível.

```
    A
   / \
  B   D
 /  
C   
```

Nesse exemplo a árvore está balanceada, por que a árvore esquerda termina no nível em que termina a direita + 1.

```
        A
       / \ 
      B   E 
     /  
    C
   /
  D   
```

Nesse exemplo a árvore está desbalanceada, por que a árvore esquerda termina no nível em que termina a direita + 2.