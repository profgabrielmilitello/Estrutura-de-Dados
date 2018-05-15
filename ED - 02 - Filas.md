Filas são estruturas de dados semelhantes a listas mas com maiores restrições.

Uma fila tem apenas 2 operações adicionar e remover.

Além disso ela tem uma regra bastante clara de como fazer isso:

**Primeiro elemento a entrar na fila é o primeiro a sair.**

Filas simulam filas da *vida real*, por exemplo em um caixa, o primeiro a chegar será atendido primeiro e assim por diante.

Abaixo temos uma implementação de uma Fila em JAVA:

```java
public class Fila{

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
        int valor = this.valores[0];
        int[] novo = new int[this.valores.length - 1];
        for(int i=0; i < novo.length; i++){
            novo[i] = this.valores[i+1];
        }
        
        this.valores = novo;
        
        return valor;
    }
    
    public void print(){
        System.out.print("[ ");
        for(int i=0; i<this.valores.length; i++){
            System.out.print(this.valores[i] + " ");
        }
        System.out.println("]");
    }
    
    public static void main(String[] args){
        Fila fila = new Fila();
        
        fila.adicionar(10);
        fila.adicionar(20);
        fila.adicionar(30);
        fila.adicionar(40);
        fila.print();
        //SAÍDA: [ 10 20 30 40 ]
        
        int x = fila.remover();
        System.out.print(x + " <- ");
        fila.print();
        //SAÍDA: 10 <- [ 20 30 40 ]
        
        x = fila.remover();
        System.out.print(x + " <- ");
        fila.print();
        //SAÍDA: 20 <- [ 30 40 ]
        
        x = fila.remover();
        System.out.print(x + " <- ");
        fila.print();
        //SAÍDA: 30 <- [ 40 ]
        
        x = fila.remover();
        System.out.print(x + " <- ");
        fila.print();
        //SAÍDA: 40 <- [ ]
        
    }

}
```