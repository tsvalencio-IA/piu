# Controle de Fiados - Android Offline

Aplicativo Android offline para controle de dívidas/fiados.

## O que faz

- Cadastro de fiados com nome, telefone, produto, quantidade, valor unitário, valor pago e observações.
- Cálculo automático de total, pago e saldo.
- Status automático: em aberto, pago parcial ou pago.
- Edição de registros.
- Recebimento parcial.
- Quitar dívida.
- Excluir registro.
- Filtros por cliente/produto/telefone e status.
- Exportar backup JSON.
- Importar backup JSON.
- Exportar planilha CSV.
- Importar planilha CSV.
- Funciona offline.
- Banco local criado automaticamente no celular.

## Banco de dados

O banco principal usa IndexedDB dentro do armazenamento interno do aplicativo Android.

Ele não é memória temporária. Os dados continuam salvos ao fechar e abrir o app.

Atenção: se o app for desinstalado ou o celular for formatado, os dados podem ser perdidos. Use Exportar JSON para guardar backup em WhatsApp, Drive, cartão ou outro local.

## Como subir no GitHub

Suba estes arquivos na raiz do novo repositório:

```text
.github/
scripts/
src/
capacitor.config.json
package.json
README.md
```

A raiz do repositório não pode ficar com uma pasta extra por cima.

## Como gerar o APK

No GitHub:

1. Abra o repositório.
2. Vá em Actions.
3. Selecione: `Gerar APK Android - Controle de Fiados`.
4. Clique em `Run workflow`.
5. Aguarde finalizar.
6. Baixe o artifact: `CONTROLE-FIADOS-ANDROID-APK`.
7. Instale o arquivo `.apk` no Android.

## Observação

O APK gerado pelo workflow é debug. Ele instala normalmente para teste interno, mas não é uma versão assinada para Play Store.

Powered by thIAguinho Soluções.


## Correção de build no GitHub Actions

Este pacote usa Capacitor CLI atual, que exige Node.js 22 ou superior.
O workflow `.github/workflows/build-android-apk.yml` já está configurado com:

```yaml
node-version: '22'
```

Se o GitHub Actions mostrar erro `The Capacitor CLI requires NodeJS >=22.0.0`, confirme que o arquivo do workflow enviado ao repositório é esta versão v2.


## Correção v3 — Java 21

Se o GitHub Actions mostrar erro `invalid source release: 21`, significa que o build Android está tentando compilar com Java 21, mas o workflow estava usando Java 17.

Esta versão já corrige o workflow para:

```yaml
node-version: '22'
java-version: '21'
```
