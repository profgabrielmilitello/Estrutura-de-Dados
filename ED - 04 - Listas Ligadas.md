## Listas Ligadas

Listas ligadas são listas em que cada nó da lista contém um valor e uma referência para o nó seguinte.

Algumas listas tem referências para o nó seguinte e para o anterior, essas listas são chamadas listas duplamente ligadas.

Também usamos o termo listas dinâmicas em oposição às listas estáticas construídas em cima de arrays.

No código abaixo temos a implementação de uma lista ligada:

```java
public class ListaLigada{

  private No primeiro;
  private int tamanho;
  
  public int getTamanho(){ return this.tamanho; }
  public No getPrimeiro(){ return this.primeiro; }
  
  public ListaLigada(){}
  public ListaLigada(int[] vetor){
    
    No atual = null;
    
    for(int i=vetor.length - 1; i >= 0; i--){
      
      No no = new No(vetor[i]);
      no.setProximo(atual);
      atual = no;
      this.tamanho++;
    }
    
    this.primeiro = atual;
  }
  
  @Override
  public String toString(){
  	if(this.tamanho == 0) return "Tamanho: "+this.tamanho+" []";
    else{
      No atual = primeiro;
      String result = "Tamanho: "+this.tamanho+" [ ";
      do{
        result += atual.getValor() + " ";
        atual = atual.getProximo();
      }while(atual != null);
      result += "]";
      return result;
    }
  }
  
  public void print(){
  	System.out.println(this);
  }
  
  public void adicionarNaFrente(No no){
    if(this.primeiro != null){
    	no.setProximo(this.primeiro);
    }
    this.primeiro = no;
    this.tamanho++;
  }
  
  public void adicionarNoFim(No no){
    if(this.primeiro == null){
    	this.primeiro = no;
    }
    else{
      No atual = primeiro;
      while(atual.getProximo() != null){
        atual = atual.getProximo();
      }
      atual.setProximo(no);
    }
    this.tamanho++;
  }
  
  public int[] toArray(){
  	int[] result = new int[this.tamanho];
    No atual = primeiro;
    for(int i=0; i<this.tamanho; i++){
    	result[i] = atual.getValor();
      	atual = atual.getProximo();
    }
    return result;
  }
  
  public int buscarPrimeiro(int valor){
    int index = 0;
    No atual = this.primeiro;
    while(atual != null){
      if(atual.getValor() == valor){
      	return index;
      }
      atual = atual.getProximo();
      index++;
    }
    return -1;
  }
  
  public int buscarUltimo(int valor){
    int index = 0;
    int result = -1;
    No atual = this.primeiro;
    while(atual != null){
      if(atual.getValor() == valor){
      	result = index;
      }
      atual = atual.getProximo();
      index++;
    }
    return result;
  }
  
  public void remover(int index){
  
    if(index == 0){
      this.primeiro = this.primeiro.getProximo();
      tamanho--;
    }
    else{
      if(index>0 && index <= this.tamanho){
        No atual = this.primeiro;
        No anterior = this.primeiro;

        for(int i=1; i < index; i++){
          anterior = atual;
          atual = atual.getProximo();
        }

        anterior.setProximo(atual.getProximo());
        tamanho--;
      }
  	}
  }
}

public class No{
  private int valor;
  private No proximo;
  
  public No(int valor){
    this.valor = valor;
  }
  
  public No(int valor, No proximo){
    this.valor = valor;
    this.proximo = proximo;
  }
  
  public int getValor(){ return this.valor; }
  public No getProximo(){ return this.proximo; }
  public void setProximo(No proximo){ this.proximo = proximo; }
}
```

Código de teste:
```java
public class Programa
{
    public static void main(String[] args)
    {
        ListaLigada lst = new ListaLigada();
        lst.print(); //Tamanho: 0 []
        
        lst.adicionarNaFrente(new No(10));
        lst.print(); //Tamanho: 1 [ 10 ]
        
        lst.adicionarNaFrente(new No(20));
        lst.print(); //Tamanho: 2 [ 20 10 ]
        
        lst.adicionarNoFim(new No(30));
        lst.print(); //Tamanho: 3 [ 20 10 30 ]
        
        lst.adicionarNaFrente(new No(20));
        lst.print(); //Tamanho: 4 [ 20 20 10 30 ]

        int index = lst.buscarPrimeiro(20);
        System.out.println("Index: " + index); //Index: 0

        index = lst.buscarUltimo(20);
        System.out.println("Index: " + index); //Index: 1

        index = lst.buscarPrimeiro(40);
        System.out.println("Index: " + index); //Index: -1



        ListaLigada lst2 = new ListaLigada(new int[]{10,20,30,40,50});
        lst2.print(); //Tamanho: 5 [ 10 20 30 40 50 ]

        lst2.remover(0);
        lst2.print(); //Tamanho: 4 [ 20 30 40 50 ]
        
        lst2.remover(4);
        lst2.print(); //Tamanho: 3 [ 20 30 40 ]
    }
}
```