import pygame
import sys

# Inicializar o Pygame
pygame.init()

# Configurações da tela
largura = 800
altura = 600
tela = pygame.display.set_mode((largura, altura))
pygame.display.set_caption("Jogo de Carro")

# Cores
BRANCO = (255, 255, 255)
AZUL = (0, 0, 255)
PRETO = (0, 0, 0)

# Carregar a imagem do carro
carro = pygame.image.load('carro.png')  # Adicione um arquivo de imagem de um carro
carro_rect = carro.get_rect()
carro_rect.center = (largura // 2, altura - 100)

# Velocidade do carro
velocidade = 5

# Loop principal do jogo
clock = pygame.time.Clock()

while True:
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Movimentação do carro
    teclas = pygame.key.get_pressed()
    if teclas[pygame.K_LEFT] and carro_rect.left > 0:
        carro_rect.x -= velocidade
    if teclas[pygame.K_RIGHT] and carro_rect.right < largura:
        carro_rect.x += velocidade

    # Preencher a tela com a cor de fundo
    tela.fill(BRANCO)

    # Desenhar o carro
    tela.blit(carro, carro_rect)

    # Atualizar a tela
    pygame.display.update()

    # Controlar a taxa de quadros por segundo (FPS)
    clock.tick(60)
