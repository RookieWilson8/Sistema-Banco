# Sistema-Banco

menu = """
[1] - Depositar
[2] - Sacar
[3] - Extrato
[4] - Sair
"""

saldo = 0
limite = 500
extrato = []
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    print(menu)
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        valor_deposito = float(input("Digite o valor do depósito: "))
        if valor_deposito > 0:
            saldo += valor_deposito
            extrato.append(f"Depósito: +R${valor_deposito:.2f}")
        else:
            print("Valor inválido. O valor do depósito deve ser maior que zero.")

    elif opcao == "2":
        if numero_saques < LIMITE_SAQUES:
            valor_saque = float(input("Digite o valor do saque: "))
            if valor_saque <= saldo and valor_saque <= limite and valor_saque > 0:
                saldo -= valor_saque
                extrato.append(f"Saque: -R${valor_saque:.2f}")
                numero_saques += 1
            else:
                print("Valor inválido ou saldo insuficiente ou valor de saque acima do limite.")
        else:
            print(f"Limite de saques ({LIMITE_SAQUES}) atingido para hoje.")

    elif opcao == "3":
        print("Extrato:")
        for movimento in extrato:
            print(movimento)
        print(f"Saldo atual: R${saldo:.2f}")

    elif opcao == "4":
        print("Saindo...")
        break

    else:
        print("Opção inválida. Por favor, escolha uma opção válida.")
