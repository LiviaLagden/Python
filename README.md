def main():
       # dados[i] = [nome, salario_bruto, genero]
    dados = [[None, 0.0, None] for _ in range(N)]

    # resultados[i] = [salario_liquido, vale_alimentacao, total]
    resultados = [[0.0, 0.0, 0.0] for _ in range(N)

    for i in range(N):
        print(f"\nFuncionário {i + 1}")
        dados[i][0] = input("Nome: ")
        dados[i][1] = float(input("Salário bruto: R$ "))
        dados[i][2] = input("Gênero (M/F): ").strip().upper()

    
    for i in range(N):
        salario_bruto = dados[i][1]
        inss = salario_bruto * 0.11
        fgts = salario_bruto * 0.05
        salario_liquido = salario_bruto - inss - fgts

        if salario_liquido < 7298.97:
            vale_alimentacao = 729.87
        else:
            vale_alimentacao = 499.78

        total = salario_liquido + vale_alimentacao

        resultados[i][0] = salario_liquido
        resultados[i][1] = vale_alimentacao
        resultados[i][2] = total

    #
    print
    for i in range(N):
        nome = dados[i][0]
        salario_liquido = resultados[i][0]
        vale_alimentacao = resultados[i][1]
        total = resultados[i][2]
        print(f"{nome} | Líquido: R$ {salario_liquido:.2f} | "
              f"Vale Alimentação: R$ {vale_alimentacao:.2f} | "
              f"Total: R$ {total:.2f}")

    qtd_masc = 0
    qtd_fem = 0
    for i in range(N):
        if dados[i][2] == "M":
            qtd_masc += 1
        elif dados[i][2] == "F":
            qtd_fem += 1

    maior_liq = resultados[0][0]
    menor_liq = resultados[0][0]
    nome_maior = dados[0][0]
    nome_menor = dados[0][0]

    for i in range(1, N):
        if resultados[i][0] > maior_liq:
            maior_liq = resultados[i][0]
            nome_maior = dados[i][0]
        if resultados[i][0] < menor_liq:
            menor_liq = resultados[i][0]
            nome_menor = dados[i][0]

    maior_liq_m = None
    maior_liq_f = None
    nome_maior_m = ""
    nome_maior_f = ""

    for i in range(N):
        if dados[i][2] == "M":
            if maior_liq_m is None or resultados[i][0] > maior_liq_m:
                maior_liq_m = resultados[i][0]
                nome_maior_m = dados[i][0]
        elif dados[i][2] == "F":
            if maior_liq_f is None or resultados[i][0] > maior_liq_f:
                maior_liq_f = resultados[i][0]
                nome_maior_f = dados[i][0]

    print
    print(f"Funcionários do gênero masculino: {qtd_masc}")
    print(f"Funcionários do gênero feminino: {qtd_fem}")
    print(f"Maior salário líquido: R$ {maior_liq:.2f} ({nome_maior})")
    print(f"Menor salário líquido: R$ {menor_liq:.2f} ({nome_menor})")

    if maior_liq_m is not None:
        print(f"Maior salário líquido (masculino): R$ {maior_liq_m:.2f} ({nome_maior_m})")
    else:
        print("Não há funcionários do gênero masculino.")

    if maior_liq_f is not None:
        print(f"Maior salário líquido (feminino): R$ {maior_liq_f:.2f} ({nome_maior_f})")
    else:
        print("Não há funcionárias do gênero feminino.")


if __name__ == "__main__":
    main()
