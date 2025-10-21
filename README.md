# Sistema de Gestão de Refeições

Sistema completo para gestão de refeições corporativas com controle de vouchers, turnos, e relatórios.

## 📋 Documentação

- **[procedimento.md](./procedimento.md)** - Guia completo de instalação e configuração
- **[executar.md](./executar.md)** - Instruções rápidas para executar o sistema

## 🚀 Início Rápido

```bash
# Instalar dependências
npm install

# Executar em desenvolvimento
npm run dev
```

Acesse: http://localhost:4173/

## 📦 Tecnologias

- React + TypeScript
- Vite
- TailwindCSS
- Supabase
- jsPDF / XLSX
- Capacitor (para Android)

## 📱 Guia Completo: Gerar APK Android Localmente

### 📋 Pré-requisitos

✅ **Java JDK 17+** (você tem Java 24 instalado)
✅ **Node.js 18+** (já instalado)

Verifique:
```bash
java -version
node -version
```

### 🚀 Comandos Passo a Passo

#### 1️⃣ Navegar para a pasta correta
```bash
cd "C:\Users\elmessonjesus.MELLOTRANSPORTE\Desktop\Sistema de Gestão de Refeições"
```

#### 2️⃣ Instalar dependências (primeira vez)
```bash
npm install
```

#### 3️⃣ Inicializar Capacitor (primeira vez)
```bash
npx cap init "Gestão de Refeições" com.mellotransporte.gestao.refeicoes --web-dir=build
```

#### 4️⃣ Adicionar plataforma Android (primeira vez)
```bash
npx cap add android
```

**Se aparecer "android platform already exists"** = Está OK! Pule para o próximo passo.

#### 5️⃣ Build do projeto web
```bash
npm run build
```

#### 6️⃣ Sincronizar com Android
```bash
npx @capacitor/cli sync
```

#### 7️⃣ Gerar o APK
```bash
cd android
.\gradlew.bat assembleDebug
```

**⏱️ Primeira vez:** 5-10 minutos (baixa dependências)
**⏱️ Próximas vezes:** 1-2 minutos

### 📦 Localizar o APK

APK gerado em:
```
android\app\build\outputs\apk\debug\app-debug.apk
```

### 🔄 Gerar Novos APKs (após alterações no código) (3 opções sem Android Studio)

#### Opção A: GitHub Actions (Recomendado - Gratuito)

1. Crie um repositório no GitHub
2. Adicione o arquivo `.github/workflows/android-build.yml`:

```yaml
name: Build Android APK
on:
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm install
      - run: npm run build
      - uses: actions/setup-java@v3
        with:
          distribution: 'zulu'
          java-version: '17'
      - uses: android-actions/setup-android@v2
      - run: npx cap sync
      - run: |
          cd android
          chmod +x gradlew
          ./gradlew assembleDebug
      - uses: actions/upload-artifact@v3
        with:
          name: app-debug
          path: android/app/build/outputs/apk/debug/app-debug.apk
```

3. Faça push do código
4. Vá em "Actions" no GitHub e execute o workflow
5. Baixe o APK dos artifacts

#### Opção B: Ionic Appflow

```bash
npm install -g @ionic/cli
ionic login
ionic link
git push ionic master
```

Acesse https://ionic.io/appflow e faça o build na nuvem.

#### Opção C: EAS Build (Expo)

```bash
npm install -g eas-cli
eas login
eas build:configure
eas build -p android --profile preview
```

### Configuração do Capacitor

Crie o arquivo `capacitor.config.ts` na raiz:

```typescript
import { CapacitorConfig } from '@capacitor/cli';

const config: CapacitorConfig = {
  appId: 'com.mellotransporte.gestao.refeicoes',
  appName: 'Gestão de Refeições',
  webDir: 'build',
  server: {
    androidScheme: 'https'
  }
};

export default config;
```

### Testar o APK

1. Transfira o APK para seu celular Android
2. Habilite "Fontes Desconhecidas" nas configurações
3. Instale e abra o aplicativo

### Personalizar Ícone

Coloque seus ícones em:
- `android/app/src/main/res/mipmap-hdpi/ic_launcher.png` (72x72)
- `android/app/src/main/res/mipmap-mdpi/ic_launcher.png` (48x48)
- `android/app/src/main/res/mipmap-xhdpi/ic_launcher.png` (96x96)
- `android/app/src/main/res/mipmap-xxhdpi/ic_launcher.png` (144x144)
- `android/app/src/main/res/mipmap-xxxhdpi/ic_launcher.png` (192x192)

### Comandos Úteis

```bash
# Build completo
npm run cap:sync

# Limpar e rebuild
cd android && gradlew.bat clean && cd ..
npm run build
npx cap sync
```

### Troubleshooting

**Tela branca ao abrir o app:**
- Verifique se `npm run build` foi executado
- Confirme que `webDir: 'build'` está correto no `capacitor.config.ts`
- Execute `npx cap sync` novamente

**App não conecta ao servidor:**
- Verifique se o servidor está acessível externamente
- Configure CORS no backend
- Adicione permissão INTERNET no `AndroidManifest.xml`

📚 **Documentação completa:** https://capacitorjs.com/docs

# Procedimento de Instalação - Sistema de Gestão de Refeições

## 📋 Pré-requisitos

Antes de iniciar, certifique-se de ter instalado:

### 1. Node.js e NPM

**Versão recomendada:** Node.js 18.x ou superior

#### Verificar se já está instalado:
```bash
node --version
npm --version
Se não estiver instalado:
Acesse: https://nodejs.org/
Baixe a versão LTS (Long Term Support)
Execute o instalador e siga as instruções
Reinicie o terminal após a instalação
🚀 Instalação do Sistema
Passo 1: Navegar para o diretório do projeto
bash
cd "c:\Users\elmessonjesus.MELLOTRANSPORTE\Desktop\Sistema de Gestão de Refeições"
Passo 2: Instalar todas as dependências
bash
npm install
O que este comando faz:

Lê o arquivo package.json
Baixa todas as bibliotecas necessárias
Cria a pasta node_modules com as dependências
Pode levar alguns minutos dependendo da conexão
Passo 3: Verificar a instalação
bash
npm list --depth=0
Este comando mostra todas as dependências principais instaladas.

⚙️ Configuração do Ambiente
Arquivo .env (se necessário)
Se o sistema usar variáveis de ambiente, crie um arquivo .env na raiz do projeto:

bash
echo. > .env
Edite o arquivo .env e adicione as configurações necessárias:

env
VITE_SUPABASE_URL=sua_url_aqui
VITE_SUPABASE_ANON_KEY=sua_chave_aqui
▶️ Executar o Sistema
Modo Desenvolvimento (Local)
bash
npm run dev
Acesso: http://localhost:4173/

Modo Desenvolvimento (Rede Local)
Para acessar de outros dispositivos na mesma rede:

bash
npm run dev -- --host
Acesso:

Local: http://localhost:4173/
Rede: http://[seu-ip-local]:4173/
🔧 Comandos Úteis
Atualizar dependências
bash
npm update
Limpar cache do NPM
bash
npm cache clean --force
Reinstalar todas as dependências
bash
# Remover node_modules e package-lock.json
rmdir /s /q node_modules
del package-lock.json

# Reinstalar
npm install
Build para produção
bash
npm run build
Preview do build de produção
bash
npm run preview
🐛 Solução de Problemas
Erro: "Cannot find module"
Solução:

bash
npm install
Erro: "EACCES: permission denied"
Solução (Windows):

Execute o terminal como Administrador
Ou limpe o cache: npm cache clean --force
Erro: "Port already in use"
Solução:

Feche outras aplicações usando a porta 4173
Ou mate o processo:
bash
netstat -ano | findstr :4173
taskkill /PID [número_do_processo] /F
Erro: "Network error" ou timeout
Solução:

Verifique sua conexão com a internet
Tente usar um proxy ou VPN diferente
Aumente o timeout:
bash
npm config set fetch-timeout 60000
Dependências desatualizadas
Verificar atualizações disponíveis:

bash
npm outdated
Atualizar para versões compatíveis:

bash
npm update
📦 Dependências Principais do Projeto
Frontend
React - Biblioteca UI
TypeScript - Tipagem estática
Vite - Build tool e dev server
TailwindCSS - Framework CSS
Lucide React - Ícones
Backend/Database
Supabase - Backend as a Service
PostgreSQL - Banco de dados
Relatórios
jsPDF - Geração de PDF
jspdf-autotable - Tabelas em PDF
XLSX - Exportação Excel
UI Components
Radix UI - Componentes acessíveis
shadcn/ui - Componentes UI
📝 Notas Importantes
Sempre execute npm install após:
Clonar o repositório
Fazer pull de novas alterações
Trocar de branch
Não commite a pasta node_modules:
Ela é gerada automaticamente
Está no .gitignore
Mantenha o Node.js atualizado:
Versões antigas podem causar problemas
Use a versão LTS recomendada
Em caso de problemas persistentes:
Delete node_modules e package-lock.json
Execute npm install novamente
📞 Suporte
Em caso de dúvidas ou problemas:

Verifique os logs de erro no terminal
Consulte a documentação das dependências
Entre em contato com o administrador do sistema
Última atualização: Outubro 2025
Versão do documento: 1.0


---

## Resumo

Criei um guia completo de instalação com:

✅ **Pré-requisitos** - Verificação e instalação do Node.js  
✅ **Instalação passo a passo** - Comandos detalhados  
✅ **Configuração** - Variáveis de ambiente  
✅ **Execução** - Modos local e rede  
✅ **Comandos úteis** - Build, update, cache  
✅ **Solução de problemas** - Erros comuns e soluções  
✅ **Dependências** - Lista completa das tecnologias  
✅ **Notas importantes** - Boas práticas  

Também atualizei o **README.md** para referenciar os dois documentos de forma organizada.