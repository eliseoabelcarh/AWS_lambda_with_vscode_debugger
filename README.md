# lambda-ts-demo

 DEPURAR LAMBDA HANDLER CON EVENTO AUTO INVOCADO (tipo "direct-invoke")

## Crear el proyecto “Hello World” (TypeScript)

Crear proyecto ejemplo

```bash
sam init \
  --name lambda-ts-demo \
  --runtime nodejs22.x \
  --app-template hello-world-typescript \
  --architecture x86_64
cd lambda-ts-demo
```


## Genera la configuración de depuración

Abrir el archivo que contiene el lambda handler

F1 → AWS: Add Local Invoke and Debug Configuration ✅

Selecciona la línea que aparece:

lambdaHandler = async (event: APIGatewayProxyEvent): Promise<...>

…esa es tu función Lambda (lambdaHandler), y es justo lo que necesitas para que el Toolkit genere la configuración adecuada.

Se creará .vscode/launch.json (tipo aws-sam).

### OPCIONAL:
cd hello-world
npm install typescript --save-dev

cd hello-world
npm install

nvm install 22

nvm use 22
nvm alias default 22


## COMPILE

Usando aws-toolkit-tsconfig.json (no usar tsconfig.json por defecto)

```bash
npx tsc --project aws-toolkit-tsconfig.json
```
Se generará app.js y app.js.map

## DEPURAR

Habilita un punto de interrupción en 

Podrás iniciar la depuración como siempre (▶️ F5 en VS Code).

Con la configuración actual (tipo "direct-invoke"), lo que hace VS Code es:

Compilar tu TypeScript con tsc.

Ejecutar sam local invoke usando el handler que configuraste.

Simular la invocación de Lambda directamente (sin levantar un endpoint HTTP).

Detenerse en tu breakpoint, si todo está bien configurado.