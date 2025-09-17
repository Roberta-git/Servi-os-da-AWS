# Guia para uso de Auto Scaling e Load Balancer

> A documentação a seguir, tem como objetivo apresentar conceitos de uso sobre alguns serviços da AWS e minhas percepções de aprendizagem.




## Índice 

1. Auto Scaling Group

   1.1 Passo a passo para criar um Auto Sacaling Group

3. Load Balancer
   
   2.1 Passo a passo para criar um Load Balancer

5. Conclusão




## 1. Auto Scaling Group 

 Auto Sacaling Group é um serviço da AWS que permite criar e gerenciar automaticamente instâncias (Ec2) de acordo com a demanda do sistema. O ASG pode iniciar novas instâncias quando a carga aumentar, garantindo que o sistema tenha capacidade suficiente para atender os usuários, e pode encerrar as instâncias quando a demanda for menor, reduzindo os custos para recursos não utilizados.
 O próprio usuário derfine um mínimno, um máximo e uma capacidade desejada de instâncias e políticas de escalonamento baseadas em métricas de monitorament (como o uso médio da CPU) para controlar quando o número de instâncias deve aumentar (scaling up) e quando deve diminuir (scaling down).

 * Scaling Up: regra que indica quando o ASG deve adicionar mais instância, usada normalmente quando uma métrica de desempenho ultrapassa um limite, como CPU, uso de memória ou tráfego.
 * Scaling Down: indica quando é necessário reduzir o número de instâncias quando a demanda cai, garantindo que recursos desnecessários não sejam pagos.

### 1.1 Passo a passo para criar um ASG

#### 1. Criar um Launch Template 

* Configure a instância Ec2 que será usada (tipo, gurpo de segurança, user data, AMI, par de chaves).


 <img src="https://github.com/user-attachments/assets/31efb97b-ced6-4156-b0ef-9a960f157a9c"  alt="" width="700"/>
</p> 



#### 2. Criar o ASG 

* Escolha o Launch template que foi criado.
* Associe as subnetes onde as instâncias serão criadas.
* Configura a capacidade míninma, máxima e desejada das instâncias.


 <img src="https://github.com/user-attachments/assets/d73ec4a8-0108-4928-991e-18982ce24764"  alt="" width="700"/>
</p> 



#### 3. Criar regras de Scaling

* Crie uma regra para scale up (ex: CPU > 70%) e uma regra para scale down (ex: CPU < 30%).
* Configure o tempo de avaliação e quantas instâncias adicionar ou remover.

#### 4. Associar o Load Balancer

* Associar o ALB ao ASC para a distribuição do tráfego entre elas e monitoramento da saúde.
  


## 2. Load Balancer

 O Load Balancer é um serviço essencial na AWS para distribuir automaticamente o tráfego de entrada entre várias instâncias Ec2, garantindo disponibilidade e escabilidade nas aplicações. Quando um Load Balancer está configurado na AWS, ele recebe as conexões dos usuários e envia essas solicitações para as instâncias EC2 que fazem parte do grupo de destino. O balanceador monitora constantemente se essas instâncias estão saudáveis através dos "exames de saúde". Se alguma delas apresentar problema ou deixar de responder, o Load Balancer deixa de encaminhar tráfego para essa instância e utiliza apenas as que continuam operando corretamente. Quando a instância problemática volta a funcionar de forma adequada, ela é automaticamente reinserida na distribuição de tráfego. Dessa forma, o funcionamento do serviço é garantido mesmo que ocorram falhas em algum dos servidores, mantendo o site ou aplicação disponível para os usuários.


 ### 2.1 Passo a passo para criar um Load Balancer

 #### 1. Criação do Load Balancer

 * No console da AWS, acesse a seção "Ec2" e depois, Load Balancer.
 * Configure o nome, Internet-facing ou internal, rede VPC, subnets e zonas de disponibilidade.


 <img src="https://github.com/user-attachments/assets/333005e6-00ac-438d-a577-b4d76336440a"  alt="" width="700"/>
</p> 


 
 #### 2. Configuração de Listeners e Target Groups

 * Escolha um "listener" (porta de entrada).
 * Crie um Target Group que receberão o tráfego do Load Balancer.


 #### 3. Associação de alvos ao Target Group 

 * Associe as instâncias Ec2 ao Target Group.
 * Verifique se o status das instãncias estão "saudáveis".

 #### 4. Verificações

 * Copie o DNS do Load Balancer, cole no navegador e verifique se há resposta.
 * Caso não funcione, reveja as configurações dos grupos de segurança, subnet e a saúde das instâncias.




## Conclusão

Com a realização deste trabalho, foi possível aprimorar o conhecimento acerca dos serviços de Auto Scaling Group e Load Balancer da AWS, compreendendos seus conceitos fundamentais e aplicações.
 



  


  
