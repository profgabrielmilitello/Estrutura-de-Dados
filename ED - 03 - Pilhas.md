Pilhas são estruturas de dados semelhantes a listas mas com maiores restrições.

Uma pilha tem apenas 2 operações adicionar e remover.

Além disso ela tem uma regra bastante clara de como fazer isso:

**Primeiro elemento a entrar na fila é o último a sair.**

Pilhas simulam pilhas da *vida real*, por exemplo uma pilha de pratos esperando ser lavados, sempre precisamos começar do de cima (último a entrar na pilha) e ir lavando prato a prato até chegar ao último.

Pilhas são muito usadas na computação porque são capazes de expressar certos tipos de dependências, por exemplo, uma função (1) chama outra função (2) que chama outra função(3) são empilhadas pelo sistema porque a 2 é dependente do resultado da 3 e a 1 é dependente do resultado da 2, portanto o computador executará 3->2->1, mesmo que a ordem de entrada seja 1->2->3. 

Abaixo temos uma implementação de uma Pilha em JAVA:

```java
public class Pilha{

    private int[] valores = new int[0];

    public void adicionar(int valor){
        int[] novo = new int[this.valores.length + 1];
        for(int i=0; i< this.valores.length; i++){
            novo[i] = this.valores[i];
        }
        novo[novo.length-1] = valor;
        
        this.valores = novo;
    }

    public int remover(){
        int valor = this.valores[this.valores.length -1];
        int[] novo = new int[this.valores.length - 1];
        for(int i=0; i < novo.length; i++){
            novo[i] = this.valores[i];
        }
        
        this.valores = novo;
        
        return valor;
    }
    
    public void print(){
        System.out.print("[ ");
        for(int i=0; i<this.valores.length; i++){
            System.out.print(this.valores[i] + " ");
        }
        System.out.print("]");
    }
    
    public void println(){
        System.out.print("[ ");
        for(int i=0; i<this.valores.length; i++){
            System.out.print(this.valores[i] + " ");
        }
        System.out.println("]");
    }
    
    public static void main(String[] args){
        Pilha pilha = new Pilha();
        
        pilha.adicionar(10);
        pilha.println();
        //SAÍDA: [ 10 ]
        
        pilha.adicionar(20);
        pilha.println();
        //SAÍDA: [ 10 20 ]
        
        pilha.adicionar(30);
        pilha.println();
        //SAÍDA: [ 10 20 30 ]
        
        pilha.adicionar(40);
        pilha.println();
        //SAÍDA: [ 10 20 30 40 ]
        
        int x = pilha.remover();
        pilha.print();
        System.out.println(" -> " + x);
        //SAÍDA: [ 10 20 30 ] -> 40
        
        x = pilha.remover();
        pilha.print();
        System.out.println(" -> " + x);
        //SAÍDA:[ 10 20 ] -> 30
        
        x = pilha.remover();
        pilha.print();
        System.out.println(" -> " + x);
        //SAÍDA: [ 10 ] -> 20
        
        x = pilha.remover();
        pilha.print();
        System.out.println(" -> " + x);
        //SAÍDA: [ ] -> 10
        
    }

}
```