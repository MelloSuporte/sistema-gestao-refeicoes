Como Executar o Sistema
Navegue para o diretório correto:
bash
cd "c:\Users\elmessonjesus.MELLOTRANSPORTE\Desktop\Sistema de Gestão de Refeições"
Execute o comando de desenvolvimento:
bash
npm run dev
Para acessar de outros dispositivos na rede (opcional):
bash
npm run dev -- --host
O sistema deve iniciar e você verá uma mensagem indicando a URL de acesso, geralmente:

Local: http://localhost:5173
Rede: http://[seu-ip]:5173 (se usar --host)
Verificação Rápida
Se você encontrar erros, verifique:

Dependências instaladas:
bash
npm install
Arquivo package.json existe:
bash
dir package.json
Node.js instalado:
bash
node --version
npm --version

# Procedimento de Instalação - Sistema de Gestão de Refeições

## 📋 Pré-requisitos

Antes de iniciar, certifique-se de ter instalado:

### 1. Node.js e NPM

**Versão recomendada:** Node.js 18.x ou superior

#### Verificar se já está instalado:
```bash
node --version
npm --version

###Se não estiver instalado:
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