---
categories: [ "code" ]
date: "2007-06-18"
title: "A inteligência do if - parte 1"
tags: [ "draft",  ]
---
No nível mais baixo, podemos dizer que as instruções de um computador se baseiam simplesmente em cálculos matemáticos e manipulação de memória. E entre os tipos de manipulação existe aquela que muda o endereço da próxima instrução que será executada. A essa manipulação damos o nome de salto.

O salto simples e direto permite a organização do código em subrotinas e assim seu reaproveitamento, o que economiza memória, mas computacionalmente é inútil, já que pode ser implementado simplesmente pela repetição das subrotinas. O que eu quero dizer é que, do ponto de vista da execução, a mesma seqüência de instruções será executada.


    subroutine                       
    +-----------------------+        
    | code                  |        
    | code                  |        
    | ...                   |        
    | code                  |        
    | return                |        
    +-----------------------+        
                                     
    routine                          
    +-----------------------+        
    |code                   |        
    |call subroutine (jump) |        
    |code                   |        
    |call subroutine (jump) |        
    |code                   |        
    |call subroutine (jump) |        
    |code                   |        
    |...                    |        
    |code                   |        
    +-----------------------+        
                        
    routine             
    +--------------+    
    | code         |    
    +--------------+    
    subroutine          
    +--------------+    
    | subroutine   |    
    | code         |    
    | code         |    
    | ...          |    
    | code         |    
    +--------------+    
    | code         |    
    +--------------+    
    subroutine      
    +--------------+
    | subroutine   |
    | code         |
    | code         |
    | ...          |
    | code         |
    +--------------+
    | code         |
    +--------------+
    subroutine      
    +--------------+
    | subroutine   |
    | code         |
    | code         |
    | ...          |
    | code         |
    +--------------+
    | code         |
    | ...          |
    | code         |
    +--------------+


A grande sacada computacional, motivo pelo qual hoje os computadores hoje são tão úteis para os seres humanos, é a invenção de um conceito chamado salto condicional. Ou seja, não é um salto certo, mas um salto que será executado caso a condição sob a qual ele está subordinado for verdadeira.

    code
    call sub *if cond true* (cond jump)
    code
    call sub *if cond true* (cond jump)
    code
    call sub *if cond true* (cond jump)
    code
    ...
    code

Os saltos condicionais, vulgarmente conhecidos como if's, permitiram às linguagens de programação possuírem construções de execução mais sofisticadas: laços, iterações e seleção de caso. Claro que no fundo elas não passam de um conjunto formado por saltos condicionais e incondicionais.

    while( condition)  
    {                 
        code;        
    }               
                   
    begin_while:
    if( condition )
    {             
        code;    
        goto begin_while;
    }                   

    
    for( i = 0; i < 10; ++i )      
    {                              
        code;                      
    }                              
                                   
    i = 0;                         
    begin_for:                     
    if( i < 10 )                   
    {                  
        code;          
        ++i;           
        goto begin_for;
    }                  


    switch( value )                
    {                              
        case 0:                    
            code;                  
            break;                 
                                   
        case 1:                    
            code;
            break;
    
        default:
            code;
            break;
    }

    if( valor == 0 ) 
        code;        
    else             
    if( valor == 1 ) 
        code;        
    else             
        code;        


Em um próximo artigo veremos como o salto condicional pode ser implementado apenas com operações matemáticas (afinal, é só isso que temos).
