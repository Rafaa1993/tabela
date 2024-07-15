def calcular_quantidade_liquido_por_hectare(area, volume, produtos): 
    try: 
        area = float(area) 
        volume = float(volume)
        
        resultados = {}
        total_liquido = 0.0
        
        for nome, quantidade_produto in produtos.items():
            quantidade_produto = float(quantidade_produto)
            quantidade_por_hectare = (volume * quantidade_produto) / area 
            resultados[nome] = quantidade_por_hectare 
            total_liquido += quantidade_por_hectare
        
        return resultados, total_liquido
    
    except ValueError: 
        return None, None

# Exemplo de utilização:
area_hectares = input("Insira a área em hectares: ")
volume_litros = input("Insira o volume de líquido aplicado (em litros): ")

produtos = {}

# Solicitar ao usuário para inserir até 3 produtos 
for i in range(1, 4): 
    nome_produto = input(f"Insira o nome do Produto {i} (ou deixe em branco para parar): ").strip()
    
    if not nome_produto:
        break
    
    quantidade_produto = input(f"Insira a quantidade do Produto {i} por hectare (em litros ou kg): ").strip()
    
    produtos[nome_produto] = quantidade_produto

quantidades_por_hectare, total_liquido = calcular_quantidade_liquido_por_hectare(area_hectares, volume_litros, produtos)

if quantidades_por_hectare is not None:
    print("\nQuantidades de líquido por hectare:")
    for nome, quantidade in quantidades_por_hectare.items():
        print(f"{nome}: {quantidade:.2f} litros")
    
    print(f"\nTotal de líquido a ser utilizado: {total_liquido:.2f} litros")
    
    # Calculando e exibindo a quantidade total de produto utilizado
    quantidade_total_produto = sum(quantidades_por_hectare.values())
    print(f"Quantidade total de produto utilizado: {quantidade_total_produto:.2f} litros")
else:
    print("Por favor, insira números válidos.")


