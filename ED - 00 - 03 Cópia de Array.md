## Cópia de arrays

Como JAVA arrays não são alocados dinamicamente, portanto, não aumentam de tamanho para acomodar mais itens, temos que muitas vezes copiá-los.

Saiba que muitas funcionalidades que vamos escrever na mão já estão prontas no JAVA (veja em java.util.Arrays).

Nosso exercício aqui é lógico, então vamos reinventar a roda um pouco. A vantagem dessa abordagem é que temos controle total de como nossa cópia funcionará.

Antes de mais nada, arrays são passados por referência, ou seja, se um array é um parâmetro de método o que será recebido dentro do método é seu endereço de memória!

Veja o código abaixo:

```java
public class ArrayPlayground{

     public static void main(String []args){
        int[] vetor = new int[]{1,2,3,4,5};
        print(vetor);
        changeArray(vetor);
        print(vetor);
        changeCopy(vetor);
        print(vetor);
     }
     
     public static void print(int[] vetor){
         for(int i=0; i< vetor.length; i++){
             System.out.print(vetor[i] + " ");
         }
         System.out.println("");
     }

    public static void changeArray(int[] vetor){
        vetor[0] = 10;
    }
    
    public static void changeCopy(int[] vetor){
        int[] copy = vetor;
        copy[0] = 20;
    }

}
```

A saída desse código é:

1 2 3 4 5

10 2 3 4 5

20 2 3 4 5 

Observe que a chamada dos métodos alterou o vetor original, mesmo quando o atribuímos a uma variável diferente em *changeCopy*.

Isso se dá porque quando fizemos int[] copy = vetor; acabamos por copiar o endereço de memória de vetor, não seus valores!

Para evitar que mudemos os valores do vetor original precisamos usar um conceito chamado *deep copy* ou cópia profunda.

Ele consiste em criar um novo array e copiar seus valores índice a índice. Observe:

```java
public class ArrayPlayground{

     public static void main(String []args){
        int[] vetor = new int[]{1,2,3,4,5};
        print(vetor);
        int[] novo = deepCopyAndChange(vetor);
        print(vetor);
        print(novo);
     }
     
     public static void print(int[] vetor){
         for(int i=0; i< vetor.length; i++){
             System.out.print(vetor[i] + " ");
         }
         System.out.println("");
     }

    public static int[] deepCopyAndChange(int[] vetor){
        
        int[] novo = new int[vetor.length];
        
        for(int i=0; i< vetor.length; i++){
             novo[i] = vetor[i];
        }
        
        novo[0] = 10;
        return novo;
    }

}
```

A saída é:

1 2 3 4 5

1 2 3 4 5

10 2 3 4 5

O que mostra que o array original não foi modificado, apenas sua cópia.
Tivemos que mudar o tipo de retorno do método pra retornar o novo array.

Podemos fazer uma cópia desse tipo para arrays menores ou maiores, abaixo 4 códigos que fazem isso:

```java
public class ArrayPlayground{

    public static void main(String []args){
        int[] vetor = new int[]{1,2,3,4,5};
        
        int[] novo = reduceAndTrimFirst(vetor); //Reduz e remove o primeiro
        print(vetor);
        print(novo);
        
        /*
        SAÍDA:
        1 2 3 4 5 
        2 3 4 5
        */
        
        novo = reduceAndTrimLast(vetor); //Reduz e remove o último
        print(vetor);
        print(novo);
        
        /*
        SAÍDA:
        1 2 3 4 5 
        1 2 3 4 
        */
        
        novo = enlargeFromBegin(vetor); //Aumenta e deixa o primeiro índice com valor padrão (0)
        print(vetor);
        print(novo);
        
        /*
        SAÍDA:
        1 2 3 4 5 
        0 1 2 3 4 5 
        */
        
        novo = enlargeFromEnd(vetor); //Aumenta e deixa o último índice com valor padrão (0)
        print(vetor);
        print(novo);
        
        /*
        SAÍDA:
        1 2 3 4 5 
        1 2 3 4 5 0  
        */
     }
     
    public static void print(int[] vetor){
         for(int i=0; i < vetor.length; i++){
             System.out.print(vetor[i] + " ");
         }
         System.out.println("");
     }

    public static int[] reduceAndTrimFirst(int[] vetor){
        int[] novo = new int[vetor.length -1];
        for(int i=0; i < novo.length; i++){
            novo[i] = vetor[i+1];
        }
        return novo;
    }
    
    public static int[] reduceAndTrimLast(int[] vetor){
        int[] novo = new int[vetor.length -1];
        for(int i=0; i < novo.length; i++){
            novo[i] = vetor[i];
        }
        return novo;
    }
    
    public static int[] enlargeFromBegin(int[] vetor){
        int[] novo = new int[vetor.length + 1];
        for(int i=0; i < vetor.length; i++){
            novo[i+1] = vetor[i];
        }
        return novo;
    }
    
    public static int[] enlargeFromEnd(int[] vetor){
        int[] novo = new int[vetor.length + 1];
        for(int i=0; i < vetor.length; i++){
            novo[i] = vetor[i];
        }
        return novo;
    }
}
```