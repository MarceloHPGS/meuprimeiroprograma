# meuprimeiroprograma
Criando Menu de Banco

print("=-="*10)
print("BANCO DA GENTE".center(30))
print("=-="*10)
print("   SEJA BEM VINDO(A)   ".center(30))

menu = """
[1] Depositar
[2] Sacar
[3] Extrato
[0] Sair
 """

saldo = 0
limite = 500
extrato = ''
num_saques = 0
LIMITE_SAQUES = 3

print("=-="*10)

while True:
    print(menu)
    print("=-="*10)
    escolha = int(input("Qual operação o Sr(a) deseja realizar? "))

    if escolha == 1:
        print("==>\033[0;33m Realizar Deposito\033[m")
        dep = float(input("Qual valor deseja depositar?R$"))
        if dep > 0:
            saldo += dep
            extrato += f"Deposito: R$ {dep:.2f}\n"
            print("\033[0;32mDeposito realizado com SUCESSO!\033[m")

        else:
            print("\033[0;31mOperação Falhou! O valor informado é inválido.\033[m")       
    elif escolha == 2:
        print("==>\033[0;33m Realizar Saque\033[m")
        saq = float(input("Qual valor deseja sacar?R$"))

        excedeu_saldo = saq > saldo
        excedeu_limite = saq > limite
        excedeu_saques = num_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("\033[0;31mOperação falhou! Saldo insuficiente.\033[m")

        elif excedeu_limite:
            print("\033[0;31mOperação falhou! Valor de saque excede o limite.\033[m")

        elif excedeu_saques:
            print("\033[0;31mOperação falhou! Número máximo de saques excedido.\033[m")

        elif saq > 0:
            saldo -= saq
            extrato += f"Saque: R$ {saq:.2f}\n"
            num_saques += 1
            print("\033[0;32mSaque realizado com SUCESSO!\033[m")

        else:
            print("\033[0;31mOperação falhou! O valor informado é inválido.\033[m")

    elif escolha == 3:
        print("==>\033[0;33m Exibir Extrato\033[m")
        print("\n\033[0;34m==========EXTRATO==========\033[m")
        print("\033[0;31mNão foram realizadas movimentações.\033[m" if not extrato else extrato)
        print(f"\n\033[0;34mSaldo: R$ {saldo:2.2f}\033[m")
        print("=" * 20)

    elif escolha == 4:
        print("\033[0;34mVOLTE SEMPRE! OBRIGADO POR UTILIZAR NOSSOS SERVIÇOS.\033[m")
        break

    else:
        print("\033[0;31mOpção inválida! Volte ao menu e escolha uma opção válida.\033[m")
         
