Listas são as estruturas de dados mais simples, que em nada se diferem dos arrays.

Normalmente as listas apresentam operações básicas como inserção, exclusão e busca.

Outras operações comuns com listas são a concatenação (a soma) de listas e a partição de uma lista em duas.

Listas podem crescer ou diminuir para acomodar seus itens.

Abaixo temos a implementação de uma lista, com as funcionalidades mais comuns e capaz de adaptar seu tamanho ao conteúdo. Também temos alguns casos de uso no método main.

Vale ressaltar que a lista abixo é uma lista estática escrita em cima de um array, listas também podem ser *ligadas* que usam ponteiros para memória (C) ou referências a objetos (JAVA).

```java
public class Lista{

    private int[] valores = new int[0];

    public int obterValorNoIndice(int indice){
        return this.valores[indice];
    }
    
    public void adicionar(int valor){
        int[] novo = new int[this.valores.length + 1];
        for(int i=0; i<this.valores.length; i++){
            novo[i] = this.valores[i];
        }
        novo[novo.length -1] = valor;
        this.valores = novo;
    }

    public void remover(int indice){
        int[] novo = new int[this.valores.length - 1];
        for(int i=0; i < indice; i++){
            novo[i] = this.valores[i];
        }
        for(int i=indice; i < this.valores.length-1; i++){
            novo[i] = this.valores[i+1];
        }
        this.valores = novo;
    }

    public int buscar(int valor){
        for(int i=0;i<this.valores.length; i++){
            if(this.valores[i] == valor){
                return i;
            }
        }
        return -1;
    }

    public void concatenar(int[] outraLista){
        int[] novo = new int[this.valores.length + outraLista.length];
        int ultimoIndice = 0;
        for(int i=0; i< this.valores.length; i++){
            novo[i] = this.valores[i];
            ultimoIndice = i;
        }
        ultimoIndice++;
        for(int i=0; i<outraLista.length; i++){
            novo[ultimoIndice + i] = outraLista[i];
        }

        this.valores = novo;
    }

    public void recortar(int inicioIncluso, int FimNaoIncluso){
        int ini = inicioIncluso;
        int fim = FimNaoIncluso;

        int[] novo = new int[fim - ini];

        for(int i=ini; i < fim; i++){
            novo[i-ini] = this.valores[i];
        }

        this.valores = novo;
    }
    
    public void print(){
        System.out.print("[ ");
        for(int i=0; i<this.valores.length; i++){
            System.out.print(this.valores[i] + " ");
        }
        System.out.println("]");
    }

    public static void main(String[] args){
        Lista lista = new Lista();
        lista.adicionar(10);
        lista.adicionar(20);
        lista.adicionar(30);
        lista.print();
        //SAÍDA: [ 10 20 30 ]
        
        lista.remover(1);
        lista.print();
        //SAÍDA: [ 10 30 ]
        
        int index = lista.buscar(10);
        System.out.println(index);
        //SAÍDA: 0
        
        index = lista.buscar(20);
        System.out.println(index);
        //SAÍDA: -1
        
        lista.concatenar(new int[]{50,60,70,80});
        lista.print();
        //SAÍDA: [ 10 30 50 60 70 80 ]
        
        lista.recortar(1,4);
        lista.print();
        //SAÍDA: [ 30 50 60 ]
    }

}
``` 