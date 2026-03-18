# FRUTESP — Gerar APK Android

## PRÉ-REQUISITOS (instalar uma vez)

1. **Node.js** → https://nodejs.org (versão 18 ou superior)
2. **Android Studio** → https://developer.android.com/studio
   - Durante a instalação marcar: Android SDK, Android SDK Platform, Android Virtual Device
3. **Java JDK 17** → https://adoptium.net

---

## ESTRUTURA DO PROJETO

```
frutesp-app/
├── www/                  ← pasta obrigatória (pode ficar vazia)
│   └── index.html        ← arquivo placeholder
├── package.json
├── capacitor.config.json ← aponta para o GitHub Pages
└── README.md
```

> O app carrega o site diretamente de https://agrotesp.github.io/Frutesp/
> Não precisa copiar nenhum arquivo HTML para a pasta www.

---

## PASSO A PASSO — PRIMEIRA VEZ

### 1. Abrir terminal na pasta frutesp-app e instalar dependências
```bash
npm install
```

### 2. Adicionar plataforma Android
```bash
npx cap add android
```

### 3. Sincronizar
```bash
npx cap sync
```

### 4. Abrir no Android Studio
```bash
npx cap open android
```

### 5. Gerar o APK
No Android Studio:
- Aguardar a sincronização terminar (barra de progresso no rodapé)
- Menu: **Build → Build Bundle(s)/APK(s) → Build APK(s)**
- Aguardar compilação
- Clicar em **"locate"** na notificação que aparecer

O APK estará em:
```
android/app/build/outputs/apk/debug/app-debug.apk
```

### 6. Instalar no celular
- Copiar o APK para o celular (WhatsApp, e-mail, cabo USB)
- No celular: Configurações → Segurança → Permitir fontes desconhecidas
- Abrir o arquivo APK e instalar

---

## ATUALIZAR O APP (quando mudar algo no site)

Quando fizer alterações no GitHub Pages, **não precisa gerar novo APK**.
O app carrega sempre a versão mais recente do site automaticamente.

Só gere um novo APK se precisar mudar:
- Nome ou ícone do app
- Permissões
- Configurações nativas

---

## GERAR APK ASSINADO (para Play Store)

Para publicar na Play Store, o APK precisa ser assinado. No Android Studio:
- **Build → Generate Signed Bundle/APK**
- Criar uma keystore (guardar o arquivo e senha — não pode perder!)
- Seguir o assistente

---

## PUBLICAR NA PLAY STORE

1. Criar conta de desenvolvedor: https://play.google.com/console
   - Taxa única de U$25 (~R$130)
2. Criar novo app
3. Preencher informações, capturas de tela, descrição
4. Upload do APK assinado
5. Publicar

---

## iOS (iPhone) — REQUISITOS EXTRAS

- Obrigatório ter um **Mac** com Xcode instalado
- Conta Apple Developer: https://developer.apple.com (~R$600/ano)

```bash
npx cap add ios
npx cap open ios
```

---

## PROBLEMAS COMUNS

**"ANDROID_HOME não encontrado"**
→ Abrir Android Studio → SDK Manager → copiar o caminho do SDK
→ Adicionar nas variáveis de ambiente do sistema

**"Gradle build failed"**
→ No Android Studio: File → Invalidate Caches → Restart

**App abre tela branca**
→ Verificar se o GitHub Pages está no ar: https://agrotesp.github.io/Frutesp/
→ Verificar conexão com internet no celular

**APK não instala no celular**
→ Ativar "Fontes desconhecidas" nas configurações do Android
→ Desinstalar versão anterior se existir
