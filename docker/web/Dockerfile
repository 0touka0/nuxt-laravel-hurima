# Node.jsの公式イメージを使用
FROM node:20

# 作業ディレクトリを指定
WORKDIR /app

# package.jsonファイルをコピー（依存関係をインストール）
COPY frontend/package*.json ./

# 依存関係をインストール
RUN npm install

# Vueのソースコードをコピー
COPY . .

# 開発サーバーを起動
CMD ["npm", "run", "dev"]

# Vue開発サーバーのポートを公開（デフォルトは5173ポート）
EXPOSE 3000