# aula-git-joao
import random

class Carta:
    def _init_(self, valor, naipe):
        self.valor = valor
        self.naipe = naipe

    def _str_(self):
        return f"{self.valor} de {self.naipe}"

class Baralho:
    def _init_(self):
        self.cartas = []
        for naipe in ['Espadas', 'Paus', 'Copas', 'Ouros']:
            for valor in range(2, 15):
                self.cartas.append(Carta(valor, naipe))

    def embaralhar(self):
        random.shuffle(self.cartas)

    def distribuir_cartas(self, num_cartas):
        return [self.cartas.pop() for _ in range(num_cartas)]

class Jogador:
    def _init_(self, nome):
        self.nome = nome
        self.mao = []

    def receber_carta(self, carta):
        self.mao.append(carta)

    def mostrar_mao(self):
        print(f"Cartas de {self.nome}:")
        for carta in self.mao:
            print(carta)

baralho = Baralho()
baralho.embaralhar()

jogador1 = Jogador("Jogador 1")
jogador2 = Jogador("Jogador 2")

num_cartas_distribuir = 5

jogador1.receber_carta(baralho.distribuir_cartas(num_cartas_distribuir))
jogador2.receber_carta(baralho.distribuir_cartas(num_cartas_distribuir))

jogador1.mostrar_mao()
jogador2.mostrar_mao()
