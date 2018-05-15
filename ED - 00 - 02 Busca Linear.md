## Busca Linear

Percorrer um vetor (array) por completo a procura de um valor específico é um conceito chamado busca linear.

A busca linear consiste em um laço de repetição que percorre cada índice e um condicional que verifica se o valor naquele índice é o que estamos procurando.

```java
public int buscaLinear(vetor, valor){
    for(int i=0; i<vetor.length; i++){
        if(vetor[i] == valor){
            return i;
        }
    }
    return -1;
}
```

O código acima realiza uma busca linear, geralmente conhecida como firstIndexOf, em português "primeiro índice de", porque ele retorna o primeiro índice i que contiver o valor buscado e encerra o algoritmo.

```java
public int buscaLinear(vetor, valor){
    int index = -1;
    for(int i=0; i<vetor.length; i++){
        if(vetor[i] == valor){
            index = i;
        }
    }
    return index;
}
```

O código acima realiza uma busca linear, geralmente conhecida como lastIndexOf, em português "último índice de", porque ele retorna o último índice i que contiver o valor buscado e não encerra o algoritmo quando encontra um deles.

Vamos falar de complexidade mais a frente, mas já tenha em mente que a complexidade de um algoritmo é equivalente à uma abstração de quanto tempo ele gastará para rodar.

Como o tempo é dependente das configurações do hardware abstraímos o tempo real da complexidade. Estamos interessados apenas em qual a relação do tempo gasto como o tamanho de nosso problema, mas não no tempo total.

Digamos que uma busca linear demore 1000 milisegundos para executar em um array de 100 posições, em uma máquina específica.
Em outra máquina uma busca idêntica demora 500 milisegundos.

Percebe como o tempo total não reflete a complexidade do algoritmo por si só? 
Poderíamos achar que a segunda máquina roda **outro** algoritmo 2x mais rápido que o da primeira!

Vamos abstrair o tempo então:

Sempre esperamos o pior dos casos: O valor buscado na última posição do array ou inexistente. Nesse caso percorremos o array inteiro em busca do valor.

Se N for o tamanho do array teremos uma complexidade O(n), ou seja, a complexidade é diretamente proporcional com o tamanho do array.

Assim, para n = 100, podemos dizer que a primeira máquina demora 1000 / n, ou seja, 10 milisegundos para percorrer cada posição.
E que a segunda máquina demora 500 /100, ou seja, 5 milisegundos para percorrer cada posição.

Em outras palavras T = O * t >> onde T é o tempo total, O é a complexidade e t é o tempo gasto em cada n.