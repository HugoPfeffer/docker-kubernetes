<p align="center">
    <img alt="Logo Codenation" src="logo.png">
</p>

<h1 align="center">
    Projeto de Kubernetes
</h1>

<h2 align="center">
    Materiais de Estudo (Compilado por Hugo Pfeffer)
</h2>

<p align="center">
    <img alt="CentOS Version" src="https://img.shields.io/badge/Linux-CentOS8-green">
    <img alt="Made By" src="https://img.shields.io/badge/Made%20By-Hugo%20Pfeffer-red">
    <img alt="License" src="https://img.shields.io/github/license/HugoPfeffer/vagrant-ansible">
</p>

</br>
</br>
<h2> Projeto </h2>

O foco deste projeto é criar um playground pessoal para fixar os conteúdos em Kubernetes e Docker que aprendi ao decorrer deste ano de 2020 através materiais encontrados na internet e nas documentações das respectivas ferramentas.

Neste projeto contem um playbook da ferramenta Ansible, onde configurar e instalar o Kubernetes, Minikube, VirtualBox e Docker no master node. 
</br></br>
<b><i>(update: 13/10/2020)</b></i></br>
Ao avançar nos meus estudos decidi migrar meu ambiente de desenvolvimento para a GCP (Google Cloud Plataform), utilizando os $300 oferecidos pela GCP para estudos. 

</br>

<h2>Ferramentas Usadas</h2>
<ul>
    <li>Minukube</li>
    <li>Vagrant</li>
    <li>Google Cloud Plataform</li>
</ul>
</br>


<h2>Conteúdo fixado</h2>
<ul>
    <li>Criar um Cluster</li>
    <li>Criar Pods</li>
    <li>Funcionamento dos serviços NodePort, ClusterIP, LoadBalancer e Ingless</li>
        <ul>
            <li>Foi implementado no projeto o Ingress Controller e os resourses para separar o tráfego de dados entre as aplicações 'portal-noticias' e 'sistema-noticias'. Sendo essa uma solução mais elegante para um problema comum.</li>
        </ul>
    <li>Funcionamento dos volumes persistentes</li>
        <ul>
            <li>Foi implementado gcePersistentDisk, porém também adicionei outro volume persistente utilizando hostPath, para praticar.</li>
        </ul>
    <!-- <li></li>
    <li></li> -->
</ul>
</br>



<!-- <h1></h1>
<h2>Planos futuros</h2> -->








