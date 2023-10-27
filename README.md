
Você pode usar os arquivos do projeto desenvolvido
na atividade da SP1, o qual subiu no GitHub. Para
isso, abra seu diretório no GitHub, clique em Code (A)
e, depois, em HTTPS (B), conforme indicado abaixo.
Utilize o botão de copiar (C) para guardar o endereço.

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/9d71005f-4dae-452c-9ca2-dc3f0353f870)


![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/831312e0-7c7b-4809-8a06-01d785b0901f)

Em seu computador, crie uma pasta chamada loja-angular.
Na barra de endereços do Windows Explorer, digite cmd para
abrir o Terminal.

Observação: você tambem pode abrir pelo terminal do Vscode.
![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/94176477-8dc8-4b7d-bebd-5740b88a04b2)

Observação: Caso não apareça assim para você é que você não configurou e tem o link abaixo para configura caso você não queira instalar novamente

https://dev.to/leticiacamposs2/como-adicionar-um-menu-de-contexto-abrir-com-vs-code-ao-windows-explorer-300j


 
![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/3ec6ff02-cc48-4554-b70f-7d7d61bc0927)

(caso n rode o ng new de alguém pesquisar o comando set execution policy)
Agora vamos abrir a pasta onde está instalado o nosso projeto Angular
Fechar o VS Code e abrir ele na pasta do projeto


![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/8f3f257c-bddd-4212-89e5-3601b7674277)





Observação: deve rodar no powershell como administrador

Então agora vamos gerar o nosso componente Login
ng generate component views/login

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/de521cd2-2ac7-499b-b18c-cbd442ec4670)

Vamos lá, aqui o Angular já gerou pra gente xyz arquivos e nesse html aqui é onde nós
iremos colocar o código da nossa tela de login que está no projeto que pedi para vocês
baixarem no começo.
Copiar o código que estiver dentro do body


Inserir na  
```<form>```
```
#userform="ngForm" (ngSubmit)="receberDados()"
```
![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/9305a6eb-2e1a-4e92-aab1-3452fd8cede4)


Então o que que nós estamos fazendo aqui?
Essa é a estrutura que utilizaremos para estarmos vinculando a inserção e o envio de
uma informação.


E ai para trabalharmos com o formulário nós utilizamos o módulo chamado Forms
Module e tudo isso estaremos configurando aqui no app.module, lembrem-se sempre
que o app.module será a mesa que estaremos modulando todas as informações, então
aqui nós estaremos fazendo a importação desse módulo

Acrescentar nos imports


```
import { FormsModule } from '@angular/forms'
imports:[
...,
...,
FormsModule
]
```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/72aed5ef-82e2-41ff-bec1-5390ac0a0d22)

O Angular ele trabalha com rotas, com caminhos que nós estaremos utilizando para
alterarmos o conteúdo do site, já que teremos os componentes header e footer padrões
e se altera somente o conteúdo. Para isso funcionar nós precisamos criar essas rotas
aqui no app-routing


![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/daef2774-67cd-4d89-af58-2d770fc0a3f4)


![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/72782ec0-2ea6-4c0a-b3ec-101ba366c35e)

Nós indicamos a rota aqui dentro desses colchetes



```
const routes: Routes = [
 { path: "", component:LoginComponent }
]
```


![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/60d03515-0fa4-4436-90a2-0254b6630225)


Agora nós vamos criar o model, ele vai servir para nós fazermos o armazenamento
desses dados e vai funcionar para conseguirmos trabalhar com classes e objetos.
Então vamos lá

Rodar comando no terminal 
```
ng generate class models/User
```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/ee8feee3-ea39-43c8-9816-d537f11f8542)


Então agora precisamos contruir nosso método construtor


```
constructor(
 public email: string,
 public senha: string
) {}
```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/3f81d634-07db-4019-a86e-8faba3d55efc)


Agora no login.component nós vamos criar um model que vai servir de base para
trabalhar com o formuálrio, vamos criar a variável userModel que vai ser um objeto da
classe User que acabamos de criar!

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/bda44731-a1da-4b79-8795-5daea49f420e)


Inserir após o``` ngOnInit()
userModel = new User("","")```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/55619bce-a75f-4969-ab6c-016a84302780)

A gente criou a classe User com seus parâmetros, certo?
Agora nós precisamos referenciar isso no nosso template, ou seja, dentro do nosso
HTML.

Precisamos informar que essas informações do form vão ser armazenadas em algum
lugar.

Então vamos fazer o seguinte
Adicionar nos inputs do form


```
<... name="email" [(ngModel)]="user.Model.email">
```
![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/561eac86-34b1-49d8-b595-11b1634b7d45)


```
<... name="senha" [(ngModel)]="user.Model.senha">
```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/21452f73-e126-4c1d-a687-d2387111cdef)

Agora precisamos criar o evento/função que irá fazer esse serviço de enviar o que
estava no input,
então aqui nós iremos colocar isso

```
receberDados() {
console.log(this.userModel)
}
```

![image](https://github.com/CTM-SENAI-134/Pc-Frameworks/assets/144062335/27ca56f9-92dc-4ccf-8c57-80028983ef5d)

Para fazer a api fake iremos usar o **JSON-server** é um modulo de aplicativo em **NodeJS** que serve como uma ferramenta de apoio para o desenvolvimento de aplicações. O seu uso é mais comum para desenvolvimento de **front-end**, em que o foco **não é projetar uma API**, mas, sim, a **interação da pessoa usuária com a aplicação**

Iremos usar um **Middleware** do **Json-server**, iremos usar um json-server modificado para login, o json-serve-auth

Documentação json-server → https://www.npmjs.com/package/json-server-auth

O json-server vai ser responsável por armazenar os dados dos usuários.
Para poder começar vamos instalar tanto o json-server como o json-server-auth com o comando:

```npm install -D json-server json-server-auth```

Se caso não der certo realizar os comandos abaixo:

```
npm install -g json-server  
npm install -g json-server json-server-auth
```

Depois de instalar, iremos criar o arquivo db.json que vai representar nosso banco de dados 

![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1d437abc-0f1a-42ab-81bd-882a5132a501/9b057152-a91d-4393-b692-1678990a7d87/Untitled.png)

Então criamos uma lista vazia dentro do arquivo db.json

```
{
	"users": []
}
```

Vamos fazer o registro dos usuários via **Postman** (que é uma interface que nós utilizamos para fazermos requisições HTTP)

Agora vamos criar o nosso serviço que vai estar fazendo a conexão com a nossa “API”

```ng generate service services/login```

Para executar e falar para o json-server enxergar o nosso db.json e rodar nossa api fake nós utilizamos o comando

```json-server db.json -m ./node_modules/json-server-auth```

![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1d437abc-0f1a-42ab-81bd-882a5132a501/f24886ec-6a07-405b-a176-215d0d74a08e/Untitled.png)

Agora vamos cadastrar um usuário trocando o método HTTP para POST e colocando o link do nossos servidor json que está rodando

![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1d437abc-0f1a-42ab-81bd-882a5132a501/c0f1b508-790a-4d41-bbc4-ca7087ffc2b4/Untitled.png)

Vai retornar pra gente um accessToken que está no formato token JWT, vamos copiar esse token

![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1d437abc-0f1a-42ab-81bd-882a5132a501/3848370e-29c3-41ad-afb0-90cecf4795b2/Untitled.png)

Agora a gente já consegue fazer o login né, então vamos fazer a importação do nosso **HTTPClientModule** no nosso **app.module** (*assim como o FormsModule*)

Eai vamos começar a fazer o nosso método de login no nosso login.service

```
import { HttpClient, HttpHeaders } from '@angular/common/http';
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import {Login} from "../models/login";
@Injectable({
  providedIn: 'root'
})
export class LoginService {
  url = "http://localhost:3000/login"
  constructor(private httpClient: HttpClient) { }
  login(user: Login): Observable<any>{
    return this.httpClient.post(this.url, JSON.stringify(user), {
      headers: new HttpHeaders({'Content-Type': 'application/json'}),
      observe: 'response',
    })
  }
}
```

Agora nós vamos declarar aqui no nosso login.component.ts que ele tem uma dependência do nosso login.service que nem a gente fez no constructor lá do login.service

![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1d437abc-0f1a-42ab-81bd-882a5132a501/f997641f-1aa2-4957-be95-f061ce940aac/Untitled.png)

Bom, agora como o sistema já sabe **quem é o service**, a gente só precisa chamar a função agora.

Aqui vai ser legal, aqui vai ser fácil, a gente vai falar assim ó: login service eu quero fazer o método de login, vou abrir parênteses pq login é uma função, ele está pedindo os dados do nosso usuário e eles estão aqui no nosso userModel né, agora lembra do Observable, que é uma função assíncrona, pra gente conseguir pegar essa resposta a gente usa o subscribe e define aqui dentro o que vai acontecer quando a gente tiver com esses dados em mãos e então vamos dar um console log nessa resposta

```
import { Component, OnInit } from '@angular/core';
import { Login } from 'src/app/models/login';
import { LoginService } from 'src/app/services/login.service';
@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent implements OnInit {
  constructor(private loginService: LoginService) { }
  ngOnInit(): void {
  }
  userModel = new Login("","")
  receberDados() {
    console.log(this.userModel)
    this.loginService.login(this.userModel).subscribe( (response) => {
      console.log("response:", response)
    }, (error) => {
      console.log(error)
    }
    )
  }
}
```

Agora nós vamos configurar as respostas dependendo da resposta que nós tivermos da nossa API. Só lembrando que dentro da resposta que nós temos da api, dentro do objeto nós temos resumidamente 3 coisas:

- Status Code: que indica o resultado da requisição
- Mensagem: que serve para detalhar possíveis erros e
- Body: que possui os dados mais importantes de resposta da API

Agora que vocês sabem o que é uma response nós vamos fazer assim, quando o usuário conseguir logar vamos mostrar Bem vindo *usuário, quando der erro nós vamos mostrar o erro embaixo do formulário

No login.component nós faremos assim

```
import { Component, OnInit } from '@angular/core';
import { Login } from 'src/app/models/login';
import { LoginService } from 'src/app/services/login.service';
@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent implements OnInit {
  constructor(private loginService: LoginService) { }
  ngOnInit(): void {
  }
  userModel = new Login("","")
  mensagem = ""
  receberDados() {
    // console.log(this.userModel)
    this.loginService.login(this.userModel).subscribe( (response) => {
      console.log("response:", response)
      console.log("O Status Code é:", response.status)
      console.log("O token de permissão é:", response.body.acessToken)
      this.mensagem = "Bem vindo " + response.body.user.nome
      console.log(this.mensagem)
    }, (error) => {
      console.log(error)
      this.mensagem = error
    }
    )
  }
}
```

Primeiro vamos criar um elemento que vai receber essa mensagem dentro da tag ``<p>`` embaixo do form

```
<main>
  <form #userform="ngForm" (ngSubmit)="receberDados()">
    <div class="campo-label">
      <label for="email">Email</label>
      <input type="email" name="email" id="campo-email" placeholder="Ex.: email@email.com"
        [(ngModel)]="userModel.email">
    </div>
    <div class="campo-label">
      <label for="senha">Senha</label>
      <input type="password" name="password" id="password" placeholder="Sua senha aqui..." [(ngModel)]="userModel.password">
    </div>
    <button type="submit">Fazer Login</button>
  </form>
  <p id="mensagem" *ngIf=" mensagem != '' ">{{mensagem}}</p>
</main>
```
Aqui estamos utilizando uma **diretiva**, caso a mensagem for direferente de null, nós mostramos ela

Agora vamos finalizar configurando o erro no **login.component.ts**

```
import { Component, OnInit } from '@angular/core';
import { Login } from 'src/app/models/login';
import { LoginService } from 'src/app/services/login.service';
@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent implements OnInit {
  constructor(private loginService: LoginService) { }
  ngOnInit(): void {
  }
  userModel = new Login("","")
  mensagem = ""
  receberDados() {
    // console.log(this.userModel)
    this.loginService.login(this.userModel).subscribe( (response) => {
      console.log("response:", response)
      console.log("O Status Code é:", response.status)
      console.log("O token de permissão é:", response.body.acessToken)
      this.mensagem = "Bem vindo " + response.body.user.nome
      console.log(this.mensagem)
    }, (error) => {
      console.log("responseErros:", error)
      this.mensagem = "Foi encontrado algum problema, tente novamente"
    }
    )
  }
}
```
