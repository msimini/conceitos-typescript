# conceitos-typescript
 
O editor consegue usar o **IntelliSense** melhor, vai ajudar a encontrar itens dentro de um objeto por exemplo.
  
```javascript
    yarn add typescript -D
    
    
    //****** adicionar novo pacote ******
    yarn add -D express
    //instalar o types para que o editor de codigo 
    //consiga entender oq o pacote consegue fazer
    yarn add -D @types/express 
    
    
    // O TS precisa de um arquivo de configuração.
    yarn tsc --init
    
    // tsconfig.json
    // change line 
    // "outDir": "./dist", 
    // vai salvar os arquivos gerados em uma pasta.
    
    //Gera arquivos TS -> JS
    yarn tsc 
```

**Quando adicionar ou não tipagem ?**

é necessário adicionar tipagem quando o arquivo não contem o contexto do que esta acontecendo.

Eg:

Arquivo de server que importa uma função de um arquivo que não possui a instancia do app(express)

index.ts:
  ```javascript
    import express from 'express';
    import { helloWorld } from './routes';
    
    const app = express();
    
    app.get('/', helloWorld);
    
    app.listen(3333);
  ```

routes.ts
  ```javascript
    import { Request, Response } from 'express'; //adicionando tipagem
    
    export function helloWorld(request: Request, response: Response) {
      return response.json({ message: 'Hello World' })
    }
   ```

**Tipando Objetos e Vetores**
  ```javascript
    interface TechObject {
      title: string;
      experience: number;
    }
    
    interface CreateUserData {
      name?: string;
      email: string;
      password: string;
      techs: Array<string | TechObject>
      // simplearray:
      // techs: string[]
    }
    
    export default function createUser({ name, email, password }: CreateUserData ){

 ```