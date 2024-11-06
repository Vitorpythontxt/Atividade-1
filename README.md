# Atividade-1

def converter_hora(hora, minuto):
    """Converte a hora de 24 horas para 12 horas e retorna a hora formatada."""
    if hora < 0:
        return None, None

    if hora == 0:
        hora_12 = 12
        periodo = 'A'
    elif hora < 12:
        hora_12 = hora
        periodo = 'A'
    elif hora == 12:
        hora_12 = 12
        periodo = 'P'
    else:
        hora_12 = hora - 12
        periodo = 'P'

    return hora_12, minuto, periodo

def exibir_hora(hora_12, minuto, periodo):
    """Exibe a hora formatada em 12 horas."""
    if hora_12 is not None and minuto is not None:
        print(f"A hora convertida é: {hora_12}:{minuto:02d} {'AM' if periodo == 'A' else 'PM'}")
    else:
        print("Encerrando o programa.")

def main():
    while True:
        try:
            hora = int(input("Digite a hora (0-23, negativo para encerrar): "))
            if hora < 0:
                exibir_hora(None, None, None)
                break

            minuto = int(input("Digite os minutos (0-59): "))
            if minuto < 0 or minuto >= 60:
                print("Minutos inválidos. Tente novamente.")
                continue

            hora_12, minuto, periodo = converter_hora(hora, minuto)
            exibir_hora(hora_12, minuto, periodo)

        except ValueError:
            print("Entrada inválida. Por favor, insira números inteiros.")

if __name__ == "__main__":
    main()
