class LojaEletronicos:
    def __init__(self):
        self.estoque = {}

    def menu(self):
        while True:
            print("\nSistema de Controle de Estoque")
            print("1. Adicionar Produto")
            print("2. Atualizar Produto")
            print("3. Excluir Produto")
            print("4. Visualizar Estoque")
            print("5. Sair")
            opcao = input("Escolha uma opção: ")

            if opcao == "1":
                self.adicionar_produto()
            elif opcao == "2":
                self.atualizar_produto()
            elif opcao == "3":
                self.excluir_produto()
            elif opcao == "4":
                self.visualizar_estoque()
            elif opcao == "5":
                print("Saindo do sistema...")
                break
            else:
                print("Opção inválida! Tente novamente.")

    def adicionar_produto(self):
        nome = input("Nome do produto: ")
        if nome in self.estoque:
            print("Produto já existe no estoque!")
        else:
            preco = float(input("Preço do produto: "))
            quantidade = int(input("Quantidade em estoque: "))
            self.estoque[nome] = {"preço": preco, "quantidade": quantidade}
            print("Produto adicionado com sucesso!")

    def atualizar_produto(self):
        nome = input("Nome do produto a ser atualizado: ")
        if nome in self.estoque:
            preco = float(input("Novo preço: "))
            quantidade = int(input("Nova quantidade: "))
            self.estoque[nome] = {"preço": preco, "quantidade": quantidade}
            print("Produto atualizado com sucesso!")
        else:
            print("Produto não encontrado!")

    def excluir_produto(self):
        nome = input("Nome do produto a ser excluído: ")
        if nome in self.estoque:
            del self.estoque[nome]
            print("Produto excluído com sucesso!")
        else:
            print("Produto não encontrado!")

    def visualizar_estoque(self):
        if self.estoque:
            print("\nEstoque Atual:")
            for nome, info in self.estoque.items():
                print(f"Produto: {nome}, Preço: R${info['preço']:.2f}, Quantidade: {info['quantidade']}")
        else:
            print("Estoque vazio!")

if __name__ == "__main__":
    loja = LojaEletronicos()
    loja.menu()
