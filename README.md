# Codigo-em-Python-Media-para-bolsa-de-estudos

def calcular_media(notas):
    return sum(notas) / 4


def validar_inscricao(notas):
    idade = int(input("Idade: "))
    renda = float(input("Renda familiar: "))

    media = calcular_media(notas)

    if media > 8:
        if idade < 18:
            categoria = "Candidato Prioritário"
        else:
            categoria = "Candidato Bolsista"
    else:
        categoria = "Não aprovado"

    if renda < 2000:
        categoria = categoria + " (Baixa renda)"

    return media, categoria


def imprimir_relatorio(nome, media, categoria):
    print("\nNome:", nome)
    print("Média:", round(media, 2))
    print("Categoria:", categoria)


while True:
    nome = input("Nome (ou sair): ")

    if nome.lower() == "sair":
        break

    notas = []

    for i in range(4):
        while True:
            nota = float(input(f"Nota {i+1}: "))
            if 0 <= nota <= 10:
                notas.append(nota)
                break
            else:
                print("Nota inválida!")

    media, categoria = validar_inscricao(notas)

    imprimir_relatorio(nome, media, categoria)
