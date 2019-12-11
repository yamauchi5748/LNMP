# ベースイメージを指定
FROM nginx:latest

RUN chown -R nginx /var/cache/nginx \
    && chown -R nginx /run

USER nginx:nginx

COPY conf.d/default.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf

# 作業ディレクトリ作成&設定
WORKDIR /var/www