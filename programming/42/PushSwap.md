Algorythme de tri, pour classer les valeurs de deux piles de données A et B.
La pile A contient une quantité aléatoire de données négatives et/ou positives, la pile B est vide.

Les instructions suivantes existent;
    sa (swap A) : intervertit les 2 premiers éléments au sommet de la pile A, ne fait rien s'il n'y en a qu'un ou aucun
    sb (swap B) : intervertit les 2 premiers éléments au sommet de la pile B, ne fait rien s'il n'y en a qu'un ou aucun
    ss : sa et sb en même temps
    pa (push A) : prend le premier élément au sommet de B et le met sur A, ne fait rien si B est vide
    pb (push B) : prend le premier élément au sommet de A et le met sur B, ne fait rien si A est vide
    ra (rotate A) : décale d'une position vers le haut tous les éléments de la pile A, le premier élément devenant le dernier
    rb (rotate B) : décale d'une position vers le haut tous les éléments de la pile B, le premier élément devenant le dernier
    rr : ra et rb en même temps
    rra (reverse rotate A) : décale d'une position vers le bas tous les éléments de la pile A, le dernier élément devenant le premier
    rrb (reverse rotate B) : décale d'une position vers le bas tous les éléments de la pile B, le dernier élément devenant le premier
    rrr : rra et rrb en même temps

![[pushswap_instructions.png]]

Dans le terminal il faut appeler le fichier "push_swap" suivi d'une suite d'entiers.
"./push_swap" 5 4 1 2 3

Pour tester mon algorythme, il faut créer un deuxième executable "checker"
"./push_swap" 5 4 1 2 3 | ./checker 5 4 1 2 3
Qui rendra "OK" ou "KO" selon si "push_swap" fonctionne

![[checker1.png]]

![[checker2.png]]

![[checker3.png]]

![[checker4.png]]

source1 : https://medium.com/@jamierobertdawson/push-swap-the-least-amount-of-moves-with-two-stacks-d1e76a71789a

source2 : https://medium.com/nerd-for-tech/push-swap-tutorial-fa746e6aba1e

source github1 : https://github.com/pvandamme/push_swap

youtube 10 min : https://www.youtube.com/watch?v=7KW59UO55TQ