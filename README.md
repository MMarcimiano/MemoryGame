#MemoryGame
'''
Mateus Henrique
Eduardo Lago
Camily Albres

'''





while True:
    iniciar = int(input("PARA INICIAR DIGITE 1 | PARA SAIR DIGITE 0: "))
    print("")

    acerto = 0
    erro = 0
    rodada = 0

    if iniciar == 1:
        rodada = 0
        acerto = 0
        erro = 0
        valores = []
        posicoes = []

        # Tabela
        import random

        aleatoria = [1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8]
        random.shuffle(aleatoria)

        for x in range(0, 16, 4):
            print(aleatoria[x], aleatoria[x + 1], aleatoria[x + 2], aleatoria[x + 3])
        print("")

        # cartas escondidas
        fechada = [1] * 16
        for x in range(0, 16, 4):
            print(fechada[x], fechada[x + 1], fechada[x + 2], fechada[x + 3])

        # Inicio de jogo
        while acerto < 8:
            print("")
            print("Escolha uma posição ")

            posicao = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
            for y in range(0, 16, 4):
                print(posicao[y], posicao[y + 1], posicao[y + 2], posicao[y + 3])
            print("")

            # ESCOLHENDO UMA CARTA
            while True:
                q = int(input("Escolha uma carta:"))
                if q >= 0 and q <= 15:
                    print("Ok!")
                    break
                else:
                    print("Escolha inválida! Escolha outra posição. ")

            # Escolhendo carta 2
            while True:
                q2 = int(input("Escolha mais uuma carta: "))
                if q2 >= 0 and q2 <= 15:
                    print("Ok!")
                    break
                else:
                    print("Escolha inválida! Escolha outra posição. ")

            if q == q2:
                print("Inválido. você escolheu a mesma posição.")
                print("")
                print("Rodadas: ", rodada)
                print("")
                for y in range(0, 16, 4):
                    print(fechada[y], fechada[y + 1], fechada[y + 2], fechada[y + 3])

            elif aleatoria[q] == aleatoria[q2]:

                # Acertos
                if fechada[q] == 0 and fechada[q2] == 0:
                    print(" ERRO. você já havia escolhido esses valores.")
                    print("")
                    print("RODADAS:", rodada)
                    print("")
                    for y in range(0, 16, 4):
                        print(fechada[y], fechada[y + 1], fechada[y + 2], fechada[y + 3])
                else:
                    print("")
                    print("Você acertou!")
                    print("")

                    acerto += 1
                    rodada += 1

                    posicoes.append(q)
                    posicoes.append(q2)
                    valores.append(aleatoria[q])

                    print("- Posições já escolhidas corretamente:", posicoes)
                    print("- Valores já escolhidos corretamente:", valores)
                    print("Rodadas: ", rodada)
                    print("")

                    fechada[q] = 0
                    fechada[q2] = 0
                    for y in range(0, 16, 4):
                        print(fechada[y], fechada[y + 1], fechada[y + 2], fechada[y + 3])

            # Erros
            else:
                print("")
                print("Você errou!")
                print("")

                erro += 1
                rodada += 1

                print("- Posições já escolhidas corretamente:", posicoes)
                print("- Valores já escolhidos corretamente:", valores)
                print("Rodadas: ", rodada)
                print("")

                for y in range(0, 16, 4):
                    print(fechada[y], fechada[y + 1], fechada[y + 2], fechada[y + 3])

        # fim de jogo
        print("")
        print(" game over ")
        print("")
        print("Seus acertos: ", acerto)
        print("Seus erros: ", erro)
        print("Tentativas:", rodada)
        print("")
        print("Sua tabela.")
        for x in range(0, 16, 4):
            print(aleatoria[x], aleatoria[x + 1], aleatoria[x + 2], aleatoria[x + 3])
        print("")
        print("--- PARABÉNS, você finalizou o game ---")
        print("")






    elif iniciar == 0:
        print("Fechando o programa...")
        break
    else:
        print("Digito incorreto! Digite 1 para iniciar OU 0 para sair...")
