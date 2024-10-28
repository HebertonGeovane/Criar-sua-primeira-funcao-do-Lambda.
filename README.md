# Criar-sua-primeira-funcao-do-Lambda.
Criar sua primeira função do Lambda Para começar a usar o Lambda, use o console do Lambda para criar uma função. Em alguns minutos, você pode criar e implantar uma função e testá-la no console.

Criar sua primeira função do Lambda.
Pré-requisitos
Cadastrar-se em uma Conta da AWS
Se você ainda não tem Conta da AWS, siga as etapas a seguir para criar sua conta Gratuita. >>> https://lnkd.in/dDaqthFy

Criar um usuário com acesso administrativo
Depois de se cadastrar em uma Conta da AWS, proteja seu Usuário raiz da conta da AWS, habilite o AWS IAM Identity Center e crie um usuário administrativo para não usar o usuário raiz em tarefas cotidianas. >>>
https://lnkd.in/dKHpZaKi

Criar uma função do Lambda hello world com o console

1️⃣ Abra a página Funções do console do Lambda.

2️⃣ Escolha a opção Criar função.

3️⃣Selecione Criar do zero.

4️⃣ No painel Informações básicas, para Nome da função, insira myLambdaFunction.

5️⃣ Em Runtime, escolha Node.js 20.x ou Python 3.12

6️⃣ Deixe arquitetura definido como x86_64 e escolha Criar função.

O Lambda cria uma função que retorna a mensagem Hello from Lambda!. O Lambda também cria um perfil de execução para sua função. Um perfil de execução é um perfil do AWS Identity and Access Management (IAM) que concede a uma função do Lambda permissão para acessar recursos e Serviços da AWS. Para sua função, o perfil criado pelo Lambda concede permissões básicas para gravar no CloudWatch Logs.

Modificar o código no console
Escolha a guia Código.
No editor de código integrado do console, você deve ver o código da função que o Lambda criou. Se você não vir a guia lambda_function.py no editor de código, selecione lambda_function.py no explorador de arquivos, conforme mostrado no diagrama a seguir.


Cole o código a seguir na guia lambda_function.py, substituindo o código que o Lambda criou.

```bash

import json
import logging

logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    
    # Get the length and width parameters from the event object. The 
    # runtime converts the event object to a Python dictionary
    length = event['length']
    width = event['width']
    
    area = calculate_area(length, width)
    print(f"The area is {area}")
        
    logger.info(f"CloudWatch logs group: {context.log_group_name}")
    
    # return the calculated area as a JSON string
    data = {"area": area}
    return json.dumps(data)
    
def calculate_area(length, width):
    return length*width

```

Selecione Implantar para atualizar a função do seu código. Quando o Lambda implementa as alterações, o console exibe um banner informando que sua função foi atualizada com sucesso.


nvocar a função do Lambda usando o console
Para invocar sua função usando o console do Lambda, primeiro você cria um evento de teste para enviar à sua função. O evento é um documento formatado em JSON contendo dois pares de valores-chave com as chaves "length" e "width".
Criar o evento de teste

1️⃣ No painel Origem do código, escolha Testar.

2️⃣ Selecione Criar novo evento.

3️⃣ Em Nome do evento, insira myTestEvent.

4️⃣ No painel Evento JSON, substitua os valores padrão colando o seguinte: 

```bash 
{
 "length": 6,
 "width": 7
}
```

5️⃣ Escolha Salvar.
Agora você testa sua função e usa o console do Lambda e o CloudWatch Logs para visualizar registros da invocação da sua função.


Para visualizar os registros de invocação da sua função no CloudWatch Logs
Abra a página Log groups (Grupos de log) do console do CloudWatch.
Escolha o nome do grupo de logs para sua função (/aws/lambda/myLambdaFunction). Esse é o nome do grupo de logs que sua função imprimiu no console.
Na guia Fluxos de log, escolha o fluxo de logs para a invocação da sua função.

Limpeza
Excluir a função: No console do Lambda, selecione a função e clique em Ações > Excluir.
Excluir o grupo de logs: No CloudWatch, selecione o grupo de logs e clique em Ações > Excluir grupo(s) de log.
Excluir a função de execução: No IAM, selecione o perfil de execução e clique em Excluir.



Acesse : https://docs.aws.amazon.com/pt_br/lambda/latest/dg/getting-started.html 

Bons estudos.



### Página de Funções 


![image](https://github.com/user-attachments/assets/046a4621-62fa-4c52-8899-80766b26f8d1)




![image](https://github.com/user-attachments/assets/d95b13fc-c513-4724-bbe4-91b0730749b6)



### Hello From Lambda
![image](https://github.com/user-attachments/assets/f8307c4f-3fda-473a-8067-252b87290dcc)


### substituindo o código que o Lambda criou
![image](https://github.com/user-attachments/assets/37595b78-9c95-48db-978a-e544b98f8d05)


### substituindo os valores Padrões
![image](https://github.com/user-attachments/assets/480fc706-d512-4571-9e19-73d5069d604c)


###  testando sua função e visualizando os registros de invocação no console

![image](https://github.com/user-attachments/assets/1b399548-6a50-44d0-b3a2-bfc3f5d548a6)

### visualizando os registros de invocação no CloudWatch Logs
![image](https://github.com/user-attachments/assets/200ccf84-117e-4492-8256-01cb4f36c7e3)

![image](https://github.com/user-attachments/assets/d3e65388-6488-432c-b1bd-628f404a1b51)




