# Banco-ete
Um banco com função de saque, depósito, aplicação e resgate.
programa {

	funcao inicio() {

	    

	    // Declaracao das variaveis escolhidas

	    

	    // Escolhi a variavel condicao com um S para setar como padrao para posteriormente

	    // se for escolhido sair do menu, seja finalizado o programa

	    caracter condicao = 'S', depositar, opcao2

	    cadeia nome, codigo_verificador

	    // Tive um problema com a informação do numero da conta, entao iniciei como 0

	    inteiro agencia, cc = 0, cp = 0, opcao

	    real saldo = 0.0, deposito = 0.0, retirarcp = 0.0, poupanca = 0.0, saque = 0.0

	    logico logica = verdadeiro

	    

	    enquanto (logica) {

	        escreva("Informe seu nome: ")

	        leia(nome)

	    

	        escreva("Informe sua agencia: ")

	        leia(agencia)

	    

	        escreva("Informe sua conta: (xxxx) ")

	        leia(cc)

	    

	        escreva("Informe um codigo verificador: ")

	        leia(codigo_verificador)

	    

	        escreva("Deseja depositar um valor? (S / N) ")

	        leia(depositar)

	        

	        // Primeiro deposito como escolha do usuario

	        se (depositar == 'S') {

	            escreva("Informe o valor de deposito: ")

	            leia(deposito)

	            saldo += deposito

	        }senao {

	            escreva("Você não tem saldo na conta")

	        }

	        // Instanciando uma conta poupanca recebendo dados da corrente

	        criar_cp(nome, agencia, cc, cp, poupanca)

	        menu()

	        leia(opcao)

	        // 5 opcoes de menu, caso seja informado qualquer valor acima de 6, vai sair do menu

	        enquanto (opcao >=1 e opcao <=5){

	            se (opcao == 1) {

	                //Exibindo informações da conta Corrente

	                exibir_cc(nome, agencia, cc, saldo)

	                escreva("\n")

	            } senao se (opcao == 2) {

	                //Sacar valor

	                saquecc(saque, saldo)

	                

	            } senao se (opcao == 3) {

	                escreva("Informe o valor de deposito: ")

	                leia(deposito)

	                saldo += deposito

	                escreva("Valor de R$", deposito, " depositado da conta\n")

	            } senao se (opcao == 4){

	                // Exibindo informações da conta poupanca

	                exibir_cp(nome, agencia, cc, poupanca)

	                escreva("\n")

	            } senao se (opcao == 5){

	                // Aplicando na conta poupanca, dependendo do valor da conta corrente

	                aplicarcp(poupanca, saldo, deposito)

	                escreva("\n")

	            } senao se (opcao == 6){

	                // Resgatar valor da conta poupança, dependendo da disponibilidade do saldo

	                escreva("Informe o valor que deseja resgatar")

	                leia(retirarcp)

	                escreva("\n")

	            } senao {

	                // qualquer valor diferente de 1, 2, 3, 4, 5 e 6, sairá do menu

	                escreva("Saindo do menu\n")

	            }

	            // Opcao de voltar ao menu

	            escreva("Deseja voltar ao menu? (S ou N) \n")

	            leia(opcao2)

	            se (opcao2 == 'S'){

	                menu()

	                leia(opcao)

	            } senao {

	                // Opcao qualquer apenas para poder encerrar

	                opcao = 9

	            }

	        }

	        

	        

	        escreva("Deseja criar outra conta? (S / N)")

	        leia(condicao)

	        se (condicao == 'S') {

	            logica = verdadeiro

	        } senao {

	            logica = falso

	        }

	        // Limpando tela

	        limpa()

	    }

	    

	}

		// Criando conta poupanca, pegando dados da corrente

	// A conta poupanca irá adicionar o valor de + 1 na conta corrente

	funcao criar_cp(cadeia nome, inteiro agencia, inteiro cp, inteiro cc, real poupanca){

	    nome = nome

	    agencia = agencia

	    cp = cc + 1

	    poupanca = poupanca

	}

	

	//Exibir conta corrente

	funcao exibir_cc(cadeia nome, inteiro agencia, inteiro cc, real saldo){

	   escreva("Nome: ", nome , "\n")

	   escreva("Agencia: ", agencia , " \n")

	   escreva("Conta: ", cc , "\n")

	   escreva("Saldo: ", saldo)

	}

	

	// Exibir conta poupanca

	funcao exibir_cp(cadeia nome, inteiro agencia, inteiro cp, real poupanca){

	   escreva("Nome: ", nome , "\n")

	   escreva("Agencia: ", agencia , " \n")

	   escreva("Polpança: ", cp , "\n")

	   escreva("Saldo: ", poupanca)

	}

	

	//Resgatar valor de conta poupanca

	funcao resgatecp(real poupanca, real saque, real saldo){

	    se (saldo >= 0.0){

	        escreva("Digite o valor do resgate: ")

	        leia(saque)

	        poupanca -= saque

	    } senao {

	        escreva("Voce não tem saldo!")

	    }

	    

	}

	

	// Depositar valor na conta poupanca

	funcao aplicarcp(real poupanca, real saldo, real deposito){

	    se (deposito < saldo){

	        escreva("Valor informado invalido, você precisa depositar algum valor em sua conta\n")

	    } senao {

	        deposito -= saldo

	        poupanca += deposito

	        escreva("Valor aplicado na poupança")

	    }

	}

	

	// Sacar valor da conta corrente

	funcao saquecc(real saque, real saldo){

	    se (saldo >= 0.0){

	        escreva("Digite o valor do saque: ")

	        leia(saque)

	        se (saque <= saldo){

	            escreva("Valor informado é menor que o disponivel\n")

	        } senao {

	            saldo = saldo - saque

	            escreva("Valor de R$", saque, " foi retirado da conta\n")

	            escreva("Valor disponivel R$", saldo, " na conta")

	        }

	    } senao {

	        escreva("Voce não tem saldo!")

	    }

	}

	

	// Menu de opcoes

	funcao menu(){

	   escreva("Deseja efetuar qual operacao?\n")

	   escreva("1 - Mostrar conta corrente\n")

	   escreva("2 - Sacar valor na conta corrente\n")

	   escreva("3 - Depositar valor na conta corrente\n")

	   escreva("4 - Mostrar dados da conta polpança\n")

	   escreva("5 - Aplicar valor na conta poupança\n")

	   escreva("6 - Resgatar valor da conta poupança\n")

	   escreva("7 - Sair do programa\n")

	}

	

}
