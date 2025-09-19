# 📄 FGV PDF Viewer - Consulta de Documentos por CPF

Uma aplicação web estática para consulta de documentos PDF através de validação de CPF, desenvolvida para a FGV.

## 🚀 Tecnologias Utilizadas

- **HTML5** - Estrutura da página
- **CSS3** - Estilização com variáveis OKLCH para cores consistentes
- **Bootstrap 5.3.2** - Framework CSS para interface responsiva
- **Vanilla JavaScript** - Lógica de validação e interações
- **Font Awesome 6.4.0** - Ícones da interface
- **PDF.js** - Visualização de documentos PDF (integrado via iframe)

## ✨ Funcionalidades

- ✅ **Validação de CPF em tempo real** com máscara automática
- ✅ **Feedback visual** para CPFs inválidos
- ✅ **Loading** durante consulta ao backend
- ✅ **Resposta positiva** - botão para abrir PDF em nova aba
- ✅ **Resposta negativa** - mensagem amigável quando documento não é encontrado
- ✅ **Design responsivo** e moderno
- ✅ **Validação matemática** completa do CPF

## 🧪 Como Testar

### CPFs de Teste

A aplicação inclui uma simulação de backend que determina a existência do PDF baseado no **último dígito do CPF**:

#### ✅ **CPF com Documento (PDF encontrado)**
**Regra**: CPFs que terminam em número **PAR** (0, 2, 4, 6, 8)


- **Resultado**: Botão "Abrir PDF em Nova Aba" aparece
- **Comportamento**: Abre o PDF em uma nova janela/taba

#### ❌ **CPF sem Documento (PDF não encontrado)**
**Regra**: CPFs que terminam em número **ÍMPAR** (1, 3, 5, 7, 9)


- **Resultado**: Mensagem "PDF não encontrado para este CPF"
- **Comportamento**: Oferece opção de nova consulta

### Fluxo de Teste

1. **Digite um CPF válido** (11 dígitos)
2. **Observe a validação** em tempo real
3. **Clique em "Pesquisar"** quando o botão estiver habilitado
4. **Aguarde o loading** (2 segundos simulando rede)
5. **Veja o resultado** baseado no CPF digitado

## 🔧 Validação de CPF

A aplicação implementa validação completa do CPF:

- **Máscara automática**: Aplica formato `000.000.000-00` conforme digitação
- **Validação matemática**: Verifica dígitos verificadores
- **Prevenção de CPFs inválidos**: Rejeita sequências como `111.111.111-11`
- **Feedback visual**: Borda vermelha e mensagem para CPFs inválidos

## 📁 Estrutura do Projeto

```
fgv-pdf-view/
├── index.html          # Página principal
└── README.md          # Documentação
```

## 🌐 Como Executar

1. **Clone ou baixe** o projeto
2. **Abra** o arquivo `index.html` em qualquer navegador moderno
3. **Teste** com os CPFs fornecidos acima

## 🔮 Simulação de Backend

Atualmente, a aplicação simula a consulta ao backend:

```javascript
// Lógica de simulação (arquivo index.html, linha ~409)
async checkPdfExists(cpf) {
    // Simula consulta ao bucket /files/{CPF}.pdf
    // Retorna true para CPFs que terminam em número par
    return parseInt(cpf.slice(-1)) % 2 === 0;
}
```

**Regra de simulação:**
- **CPF termina em PAR** (0, 2, 4, 6, 8) → `true` (documento encontrado)
- **CPF termina em ÍMPAR** (1, 3, 5, 7, 9) → `false` (documento não encontrado)

**Para produção**, substitua esta função por uma chamada real ao seu backend que verifique a existência do arquivo no bucket `/files/{CPF}.pdf`.

## 🎨 Design

- **Cores**: Utiliza modelo OKLCH para consistência visual
- **Responsivo**: Funciona em desktop, tablet e mobile
- **Acessibilidade**: Contraste adequado e navegação por teclado
- **UX**: Feedback visual claro e transições suaves

## 📝 Próximos Passos

Para integrar com backend real:

1. Substituir `checkPdfExists()` por chamada HTTP
2. Configurar URL do bucket de arquivos
3. Implementar tratamento de erros de rede
4. Adicionar autenticação se necessário

---

**Desenvolvido para FGV** 🎓
