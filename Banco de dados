CREATE TABLE Cliente(
 ID_cliente INT PRIMARY KEY,
 nome VARCHAR(70),
 cpf CHAR(15) NOT NULL UNIQUE,
 rg CHAR(15) NOT NULL UNIQUE,
 endereco VARCHAR (50),
 cidade VARCHAR (50),
 cep CHAR(9),
 email VARCHAR(40),
 telefone CHAR(14),
 data_nascimento DATE,
 genero VARCHAR (20)
);

INSERT INTO Cliente (ID_cliente, nome, cpf, rg, endereco, cidade, cep, email, telefone, data_nascimento, genero) VALUES
(1, 'Silvana Lino De Sena', '297.238.258-10', '36.864.253-2', 'Rua Joao Guilherme Peixoto Nº100, ', 'São Paulo', '04932-120', 'Sill_123@gmail.com', '(11)96422-6054', '07-01-1992', 'Feminino'),
(2, 'Guilherme Pereira Da Silva', '329.529.702-13', '22.647.804-5', 'Rua Napoleão Nº47', 'São Paulo', '12313-176', 'Guilherme.pepe@gmail.com', '(11)95532-0642', '16-09-1999', 'Masculino'),
(3, 'Diego Santos Camargo', '743.521.820-90', '49.631.186-4', 'Rua Ibirapuera Nº471', 'São Paulo', '79802-149', 'Diego1910@gmail.com', '(11)91910-2012', '04-11-2001', 'Masculino'),
(4, 'Pedro Freitas Souza', '532.741.843-22', '62.512.164.7', 'Rua Ana Charsan Nº13', 'Osasco', '06882-002', 'Pedro_freitas@gmail.com', '(11)99328-5019', '22-10-1995', 'Masculino'),
(5, 'Vinicius Santos De Paula', '495.631.539-25', '78.662.901-4', 'Rua Paula Azevedo Melin Nº07', 'Guarulhos', '29037-419', 'Vini07@gmail.com', '(11)94264-1832', '11-03-2000', 'Masculino')

CREATE TABLE Vendedor(
 ID_vendedor INT PRIMARY KEY,
 meta_mes DECIMAL(10,2) NOT NULL,
 comissao DECIMAL (10,2) NOT NULL
 );

INSERT INTO Vendedor (ID_vendedor, meta_mes, comissao) VALUES
(1, 45000.00, 2250.00),
(2, 45000.00, 2250.00),
(3, 45000.00, 2250.00)

CREATE TABLE Forma_pagamento (
ID_forma_pagamento INT PRIMARY KEY,
 descricao VARCHAR(20) NOT NULL,
 tipo_pagamento VARCHAR(10) NOT NULL,
 qtd_parcelas VARCHAR(10)
);

INSERT INTO Forma_pagamento(id_forma_pagamento, descricao, tipo_pagamento, qtd_parcelas) VALUES
(1, 'credito', 'parcelado', '3x'),
(2, 'debito', 'a vista', '0'),
(3, 'credito', 'parcelado', '5x'),
(4, 'pix', 'a vista', '0'),
(5, 'credito', 'parcelado', '2x'),
(6, 'dinheiro', 'a vista', '0')

CREATE TABLE Registro_pagamento(
 ID_pagamento INT PRIMARY KEY,
 ID_cliente INT NOT NULL,
 ID_forma_pagamento INT NOT NULL,
 data DATE,
 valor DECIMAL(10,2),
 status VARCHAR(20),
 FOREIGN KEY (ID_cliente) REFERENCES Cliente(ID_cliente),
 FOREIGN KEY (ID_forma_pagamento) REFERENCES Forma_pagamento(ID_forma_pagamento)
);

INSERT INTO Registro_pagamento(ID_pagamento, ID_cliente, ID_forma_pagamento, data, valor, status) VALUES
(1, 1, 1, '22-07-2024', 649.80, 'concluido'),
(2, 2, 2, '23-07-2024', 629.70, 'concluido'),
(3, 3, 3, '24-07-2024', 649.60, 'concluido'),
(4, 4, 4, '24-07-2024', 529.80, 'concluido'),
(5, 5, 5, '28-07-2024', 1139.90, 'concluido'),
(6, 4, 6, '05-08-2024', 3500.00, 'pendente')

CREATE TABLE Venda(
 ID_venda INT PRIMARY KEY,
 ID_cliente INT NOT NULL,
 ID_vendedor INT NOT NULL,
 ID_pagamento INT NOT NULL
 );

 INSERT INTO Venda(ID_venda, ID_cliente, ID_vendedor, ID_pagamento) VALUES
 (1, 1, 3, 1),
 (2, 2, 1, 2),
 (3, 3, 1, 3),
 (4, 4, 2, 4),
 (5, 5, 3, 5),
 (6, 4, 2, 6)

 CREATE TABLE Pedido(
  ID_pedido INT PRIMARY KEY,
  ID_cliente INT NOT NULL,
  ID_vendedor INT NOT NULL,
  ID_pagamento INT NOT NULL,
  data_pedido DATE,
  data_entrega DATE,
  cep CHAR(9),
  frete DECIMAL(10,2),
  Status VARCHAR(20),
  FOREIGN KEY (ID_cliente) REFERENCES Cliente(ID_cliente),
  FOREIGN KEY (ID_vendedor) REFERENCES Vendedor(ID_vendedor),
  FOREIGN KEY (ID_pagamento) REFERENCES Registro_pagamento(ID_pagamento)
);

INSERT INTO Pedido(ID_pedido,ID_cliente,ID_vendedor,ID_pagamento, Data_pedido, Data_entrega, Cep, Frete, Status)
VALUES
(1, 5, 3, 5,'28-07-2024','02-08-2024','29037-419', 40.00,'Concluido'),
(2, 4, 1, 6,'05-08-2024','09-08-2024','06325-854',23.00,'Pendente')


CREATE TABLE Categoria (
ID_categoria INT PRIMARY KEY,
nome_categoria VARCHAR(80)
);

INSERT INTO Categoria (ID_categoria, nome_categoria) VALUES
 (1, 'Camisa Polo Shirt'),
 (2, 'Camisa Hawaiian'),
 (3, 'Dress Shirt manga comprida'),
 (4, 'Calça Sarja Slim'),
 (5, 'Calça Social Alfaiataria classica'),
 (6, 'Bermuda chino'),
 (7, 'Bermuda jeans'),
 (8, 'Casaco de lã'),
 (9, 'Jaqueta de Couro'),
 (10, 'Kit Cueca Boxe'),
 (11, 'Cinto Social')

 CREATE TABLE Fornecedor (
  ID_fornecedor INT PRIMARY KEY,
  nome VARCHAR(100),
  cnpj CHAR(18),
  cep CHAR(9),
  endereco VARCHAR(50),
  cidade VARCHAR(30),
  email VARCHAR(70),
  telefone CHAR(14)
  );
  
 INSERT INTO Fornecedor (id_fornecedor, nome, cnpj, cep, endereco, cidade, email, telefone) VALUES
  (01, 'Panonovo', '24.681.012/1416-18', '04932-122', 'Rua das Flores N°55', 'São Paulo', 'pano.novo@gmail.com', '(11)94002-2892'),
  (02, 'Novamoda', '13.579.111/3333-19', '04933-456', 'Avenida Brigadeiro N°76', 'Rio de Janeiro', 'nova.moda@icloud.com', '(21)91005-3479'),
  (03, 'Men´sstyle', '56.908.419/5372-26', '04992-752', 'Rua Marques Albuquerque N°90', 'São Paulo', 'mean´s.style@gmail.com', '(11)98027-8824');

CREATE TABLE Produto (
 ID_produto INT PRIMARY KEY,
 ID_fornecedor INT NOT NULL,
 ID_categoria INT NOT NULL,
 nome_produto VARCHAR(80),
 codigo_barras VARCHAR(25),
 tamanho CHAR(2),
 cor VARCHAR(20),
 preco_uni DECIMAL(10,2),
 qtd_pedida VARCHAR(10),
 uni_vendida VARCHAR(10),
 FOREIGN KEY (ID_fornecedor) REFERENCES Fornecedor (ID_fornecedor),
 FOREIGN KEY (ID_categoria) REFERENCES Categoria (ID_categoria)
);

INSERT INTO Produto(ID_produto, ID_fornecedor, ID_categoria, nome_produto, codigo_barras, tamanho, cor, preco_uni, qtd_pedida, uni_vendida) VALUES
(1, 1, 1, 'Polo Shirt preta', '10112577P02', 'P', 'preta', 179.90, '2', '1'),
(2, 1, 1, 'Polo Shirt preta', '10112577G02', 'G', 'preta', 179.90, '1', '0'),
(3, 1, 1, 'Polo Shirt branca', '10112577P1366', 'P', 'branca', 179.90, '1', '0'),
(4, 1, 1, 'Polo Shirt branca', '10112577M1366', 'M', 'branca', 179.90, '1', '1'),
(5, 2, 2, 'Camisa Hawaiian Havaiana', '11025743P227', 'P', 'Havaiana', 199.90, '1', '0'),
(6, 2, 2, 'Camisa Hawaiian Havaiana', '11025743G227', 'G', 'Havaiana', 199.90, '1', '1'),
(7, 2, 2, 'Camisa Hawaiian Floral', '11025743P228', 'P', 'Floral', 219.90, '1', '1'),
(8, 3, 3, 'Dress Shirt manga comprida azul', '12000932M08', 'M', 'Azul', 349.90, '3', '1'),
(9, 3, 3, 'Dress Shirt manga comprida azul', '12000932G08', 'G', 'Azul', 349.90, '1', '1'),
(10, 3, 3, 'Dress Shirt manga comprida cinza', '12000932M111', 'M', 'Cinza', 349.90, '2', '1'),
(11, 2, 4, 'Calça Sarja Slim gelo', '40798531381981', '38', 'Gelo', 249.90, '2', '0'),
(12, 2, 4, 'Calça Sarja Slim gelo', '40798531401981', '40', 'Gelo', 249.90, '2', '1'),
(13, 2, 4, 'Calça Sarja Slim gelo', '40798531421981', '42', 'Gelo', 249.90, '1', '0'),
(14, 2, 4, 'Calça Sarja Slim cinza chumbo', '40798531381000', '38', 'Gelo', 249.90, '2', '0'),
(15, 2, 4, 'Calça Sarja Slim cinza chumbo', '40798531401000', '40', 'Gelo', 249.90, '2', '1'),
(16, 2, 5, 'Calça Social Alfaiataria classica cinza escuro ', '412754224003', '40', 'Cinza', 349.90, '2', '1'),
(17, 1, 6, 'Bermuda chino beje', '200542174066', '40', 'Beje', 229.90, '1', '0'),
(18, 1, 6, 'Bermuda chino beje', '200542174466', '44', 'Beje', 229.90, '1', '0'),
(19, 1, 7, 'Bermuda jeans preta', '202110994202', '42', 'Preta', 199.90, '1', '0'),
(20, 2, 8, 'Casaco de lã preta', '78652175P02', 'P', 'Preta', 399.90, '1', '0'),
(21, 2, 8, 'Casaco de lã preta', '78652175M02', 'M', 'Preta', 399.90, '1', '1'),
(22, 2, 8, 'Casaco de lã cinza', '78652175M111', 'M', 'Cinza', 399.90, '1', '0'),
(23, 2, 9, 'Jaqueta de Couro', '79912254M2999', 'M', 'Couro', 3500.00, '1', '1'),
(24, 3, 10, 'Kit 3 Cueca Boxer preta', '30001916M02', 'M', 'Preta', 79.90, '4', '2'),
(25, 3, 10, 'Kit 3 Cueca Boxer preta', '30001916G02', 'G', 'Preta', 79.90, '1', '0'),
(26, 3, 10, 'Kit 3 Cueca Boxer branca', '30001916M1366', 'M', 'Branca',79.90, '2', '1'),
(27, 3, 11, 'Cinto Social Preto', '57210002M02', 'M', 'Preta', 139.90, '1', '1'),
(28, 3, 11, 'Cinto Social Preto', '57210002G02', 'G', 'Preta', 139.90, '1', '0'),
(29, 3, 11, 'Cinto Social Marrom', '57210002M55', 'M', 'Preta', 139.90, '1', '1')

CREATE TABLE Estoque(
 ID_estoque INT PRIMARY KEY,
 ID_produto INT NOT NULL,
 qtd_produto VARCHAR(5),
 FOREIGN KEY (ID_produto) REFERENCES produto (ID_produto)
);

INSERT INTO Estoque(ID_estoque, ID_produto, qtd_produto) VALUES
(1, 1, '1'),
(2, 2, '1'),
(3, 3, '1'),
(4, 4, '0'),
(5, 5, '1'),
(6, 6, '0'),
(7, 7, '0'),
(8, 8, '2'),
(9, 9, '0'),
(10, 10, '1'),
(11, 11, '2'),
(13, 13, '1'),
(14, 14, '2'),
(15, 15, '1'),
(16, 16, '1'),
(17, 17, '1'),
(18, 18, '1'),
(19, 19, '1'),
(20, 20, '1'),
(21, 21, '0'),
(22, 22, '1'),
(23, 23, '0'),
(24, 24, '2'),
(25, 25, '1'),
(26, 26, '1'),
(27, 27, '0'),
(28, 28, '1'),
(29, 29, '0')

CREATE TABLE Item_pedido(
 ID_numero_pedido INT PRIMARY KEY,
 ID_pedido INT NOT NULL,
 ID_produto INT NOT NULL,
 FOREIGN KEY (ID_pedido) REFERENCES Pedido (ID_pedido),
 FOREIGN KEY (ID_produto) REFERENCES Produto (ID_produto)
);

INSERT INTO Item_pedido (ID_numero_pedido, ID_pedido, ID_produto) VALUES
(1, 1, 7),
(2, 1, 10),
(3, 1, 16),
(4, 1, 26),
(5, 1, 27),
(6, 2, 23)

CREATE TABLE Promocao(
ID_Promocao INT PRIMARY KEY,
ID_Produto INT,
descricao_promocao VARCHAR(100),
desconto_percentual VARCHAR(100),
data_inicio DATE,
data_fim DATE
FOREIGN KEY (ID_produto) REFERENCES Produto (ID_produto)
);

INSERT INTO Promocao (ID_promocao, ID_produto, descricao_promocao, desconto_percentual, data_inicio, data_fim) VALUES
(1 , 1 , 'desconto 20% em qualquer camiseta polo' , '  20% ' , '24-05-2024' , '30-06-2024'),
(2, 19, '40% OFF no site para bermudas jeans', ' 40% ' , '06-06-2024', '04-07-2024')

CREATE TABLE Compra_produto (
 ID_compra INT PRIMARY KEY,
 ID_produto INT NOT NULL,
 preco_compra DECIMAL(10,2),
 data_compra DATE,
 FOREIGN KEY (ID_produto) REFERENCES Produto(ID_produto)
);

INSERT INTO Compra_produto (ID_compra, ID_produto, preco_compra, data_compra) VALUES
(1, 1, 49.90, '10.05.2024'),
(2, 2, 49.90, '11.05.2024'),
(3, 3, 49.90, '12.05.2024'),
(4, 4, 49.90, '13.05.2024'),
(5, 5, 69.90, '14.05.2024'),
(6, 6, 69.90, '15.05.2024'),
(7, 7, 74.90, '16.05.2024'),
(8, 8, 79.90, '17.05.2024'),
(9, 9, 79.90, '18.05.2024'),
(10, 10, 79.90, '19.05.2024'),
(11, 11, 77.90, '20.05.2024'),
(12, 12, 77.90, '21.05.2024'),
(13, 13, 77.90, '22.05.2024'),
(14, 14, 77.90, '23.05.2024'),
(15, 15, 77.90, '24.05.2024'),
(16, 16, 80.00, '25.05.2024'),
(17, 17, 60.00, '26.05.2024'),
(18, 18, 60.00, '27.05.2024'),
(19, 19, 40.00, '28.05.2024'),
(20, 20, 90.00, '29.05.2024'),
(21, 21, 90.00, '30.05.2024'),
(22, 22, 90.00, '01.05.2024'),
(23, 23, 1000.00, '02.05.2024'),
(24, 24, 19.90, '03.05.2024'),
(25, 25, 19.90, '04.05.2024'),
(26, 26, 19.90, '05.05.2024'),
(27, 27, 34.90, '06.05.2024'),
(28, 28, 34.90, '07.05.2024'),
(29, 29, 34.90, '08.05.2024')

CREATE TABLE Devolucao(
 ID_devolucao INT PRIMARY KEY,
 ID_venda INT NOT NULL,
 ID_produto INT NOT NULL,
 quantidade INT,
 data_devolucao DATE,
 motivo VARCHAR(40),
 FOREIGN KEY (ID_venda) REFERENCES Venda (ID_venda),
 FOREIGN KEY (ID_produto) REFERENCES produto (ID_produto)
);

INSERT INTO Devolucao(ID_devolucao, ID_venda, ID_produto, quantidade, data_devolucao, motivo)VALUES
(1, 3, 15, 1, '12-08-2024', 'Calça sem ziper'),
(2, 1, 21, 1, '13-08-2024', 'Casaco de lã com fios puxados'), 
(3, 4, 4, 1, '16-08-2024', 'Polo sem botão e gola suja')



SELECT * FROM Devolucao
