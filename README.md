# Guia para uso de Auto Scaling e Load Balancer

> A documentação a seguir, tem como objetivo apresentar conceitos de uso sobre alguns serviços da AWS e minhas percepções de aprendizagem.




## 1. Auto Scaling Group 

 Auto Sacaling Group é um serviço da AWS que permite criar e gerenciar automaticamente instâncias (Ec2) de acordo com a demanda do sistema. O ASG pode iniciar novas instâncias quando a carga aumentar, garantindo que o sistema tenha capacidade suficiente para atender os usuários, e pode encerrar as instâncias quando a demanda for menor, reduzindo os custos para recursos não utilizados.
 O próprio usuário derfine um mínimno, um máximo e uma capacidade desejada de instâncias e políticas de escalonamento baseadas em métricas de monitorament (como o uso médio da CPU) para controlar quando o número de instâncias deve aumentar (scaling up) e quando deve diminuir (scaling down).

 * Scaling Up: regra que indica quando o ASG deve adicionar mais instância, usada normalmente quando uma métrica de desempenho ultrapassa um limite, como CPU, uso de memória ou tráfego.
 * Scaling Down: indica quando é necessário reduzir o número de instâncias quando a demanda cai, garantindo que recursos desnecessários não sejam pagos.

### 1.1 Passo a passo para criar um ASG

#### 1. Criar um Launch Template 

* Configure a instância Ec2 que será usada (tipo, gurpo de segurança, user data, AMI, par de chaves).


#### 2. Criar o ASG 

* Escolha o Launch template que foi criado.
* Associe as subnetes onde as instâncias serão criadas.
* Configura a capacidade míninma, máxima e desejada das instâncias.

#### 3. Criar regras de Scaling

* Crie uma regra para scale up (ex: CPU > 70%) e uma regra para scale down (ex: CPU < 30%).
* Configure o tempo de avaliação e quantas instâncias adicionar ou remover.

#### 4. Associar o Load Balancer

* Associar o ALB ao ASC para a distribuição do tráfego entre elas e monitoramento da saúde.

  
