import math
import os
import time

def animar_cobra():
    # Define o tamanho do terminal virtual para a animação
    largura = 50
    comprimento_cobra = 12
    passo = 0
    
    # Limpa a tela antes de começar (funciona em Windows, Linux ou Web)
    os.system('cls' if os.name == 'nt' else 'clear')
    
    print("Pressione CTRL+C para parar a cobra.\n")
    
    try:
        while True:
            # Lista para guardar as posições de cada segmento do corpo
            corpo = []
            
            for i in range(comprimento_cobra):
                # O uso do seno (sin) faz o efeito de onda/ondulação
                # Multiplicamos o i para dar o efeito de curvas no corpo
                angulo = (passo - i) * 0.5
                posicao_x = int((largura / 2) + math.sin(angulo) * 12)
                corpo.append(posicao_x)
            
            # Desenha a linha atual baseada na cabeça da cobra (o primeiro item)
            cabeca_x = corpo[0]
            linha = [" "] * largura
            
            # Renderiza o corpo com '.' e a cabeça com 'O'
            for idx, x in enumerate(corpo):
                if 0 <= x < largura:
                    linha[x] = "O" if idx == 0 else "·"
            
            # Imprime a linha na tela
            print("".join(linha))
            
            # Avança o passo para dar movimento e espera um pouco
            passo += 1
            time.sleep(0.05)
            
    except KeyboardInterrupt:
        print("\nAnimação encerrada.")

if __name__ == "__main__":
    animar_cobra()
