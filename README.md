# Gerador de CPF utilizando Python

## Código comentado:
import random

cont_regressiva = 10
cont_regressiva_2 = 11
result_soma = result_soma_2 = 0
nove_digitos = ''

while True:
    for i in range(0, 9):
        nove_digitos += str(random.randint(0, 9)) # Concatenação de cada dígito gerado

    for num in nove_digitos: # Multiplicação regressiva do CPF
        num_int = int(num) # Conversão de str para int --> Para poder ser realizado o cálculo
        result_soma += num_int * cont_regressiva  # Cálculo do resultado de cada dígito do CPF por 10 regressivamente
        cont_regressiva -= 1 # Subtração para contagem regressiva de 10

    primeiro_digito = (result_soma * 10) % 11 # Calculo para ter o primeiro dígito validador

    if primeiro_digito > 9: # Se o primeiro dígito validador for maior que 9
        primeiro_digito = 0 # O segundo dígito vira 0

    dez_digitos = nove_digitos + str(primeiro_digito) # Concatenação dos 9 dígitos gerados mais o primeiro calculado

    for num_seg in dez_digitos: # Multiplicação regressiva do CPF        
        num_seg_int = int(num_seg) # Conversão de str para int --> Para poder ser realizado o cálculo
        result_soma_2 += num_seg_int * cont_regressiva_2 # Cálculo do resultado de cada dígito do CPF por 10 regressivamente
        cont_regressiva_2 -= 1 # Subtração para contagem regressiva de 10

    segundo_digito = (result_soma_2 * 10) % 11 # Calculo para ter o primeiro dígito validador

    if segundo_digito > 9: # Se o segundo dígito validador for maior que 9
        segundo_digito = 0 # O segundo dígito vira 0

    cpf_final = dez_digitos + str(segundo_digito) # Concatenação adicionando o segundo dígito validador
    # O CPF final terá 11 dígitos, sendo os 9 primeiros gerados aleatóriamente e os 2 últimos validados através de cálculo
    print(cpf_final)
    break
