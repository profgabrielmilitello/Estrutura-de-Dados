## Arrays (Vetores)

Arrays ou Vetores são estruturas de dados existentes em todas as linguagens de programação.

São tipos de dados capazes de armazenar vários valores do mesmo *tipo*. (válido para linguagens fortemente tipadas)

O acesso a cada valor armazenado se dá por um *index* (índice) que começa em 0 e aponta para primeiro item no vetor, e termina em [tamanho - 1] que aponta para o último item.

Entre o index 0 e o index [tamanho - 1] existe qualquer quantidade de valores, contanto que caibam na memória da máquina.

Como sempre sabemos o primeiro e último índices do vetor podemos acessar todos os valores usando um laço de repetição.

No JAVA, vetores não tem alocação dinâmica, ou seja, precisamos inicializá-lo usando um valor inteiro que determina seu tamanho.

Para aumentar um vetor precisamos declarar um novo vetor com tamanho [tamanho do antigo + 1], copiar o antigo, e subtituí-lo pelo novo.

Vejamos alguns exemplos:

```java
int[] vetor1 = new int[5]; //Declara e aloca memória para um vetor de inteiros de 5 posições
int[] vetor2 = new int[10]; //Declara e aloca memória para um vetor de inteiros de 10 posições
float[] vetor3 = new float[10]; //Declara e aloca memória para um vetor de floats de 10 posições
String[] vetor4 = new String[3]; //Declara e aloca memória para um vetor de String de 3 posições  
```

Os códigos acima são todos de declaração de vetores, observe que definimos o tipo e o tamanho do vetor.
Assim, o JAVA sabe quanta memória alocar, por exemplo, um vetor de int de 10 posições alocará [2^32 * 10] tamanho de um int na memória (2^32) * tamanho do vetor (10).

Mais exemplos:

```java
int[] vetor = new int[] {1,2,3,4,5}; //Inicialização de vetores com valores
```

No código acima não passamos o tamanho do vetor, mas sim os valores que ele deve conter.
O java consegue inferir pela quantidade de valores qual será o tamanho do vetor.

```java
int[] vetor = new int[] {1,2,3,4,5};
System.out.println(vetor[0]);
System.out.println(vetor[1]);
System.out.println(vetor[2]);
System.out.println(vetor[3]);
System.out.println(vetor[4]);

//Saída: 12345
```

O código acima imprime o array, observe que o primeiro índice é 0 e o último é tamanho - 1 (5-1) = 4;

 ```java
int[] vetor = new int[] {1,2,3,4,5};
for(int i=0; i < vetor.length; i++){
    System.out.println(vetor[i]);
}
//Saída: 12345
```

O código acima faz exatamente a mesma coisa que o anterior, mas usando um laço. 
Ele tem a vantagem de poder percorrer arrays de qualquer tamanho, porque ele lê o tamanho em *vetor.length*.
Observe que usamos **<** dentro do for portanto não precisamos fazer vetor.length - 1, o que seria necessário se tivesse sido usado **<=**.

```java
int[] vetor = new int[5];
vetor[0] = 1;
vetor[1] = 2;
vetor[2] = 3;
vetor[3] = 4;
vetor[4] = 5;
```

O código acima preenche manualmente o vetor com valores.

```java
int[] vetor = new int[5];
for(int i=0; i<vetor.length; i++){
    vetor[i] = i+1;
}
```

O código acima faz a mesma coisa que o anterior.
No entanto, só é possível preencher o vetor assim se usarmos um valor único (0 por exemplo) ou um valor que tenha relação com i (i+1 por exemplo).


