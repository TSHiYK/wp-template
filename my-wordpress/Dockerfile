FROM wordpress:latest

# 必要なツール群をインストール
RUN apt-get update
RUN apt-get -y install wget unzip

# WPプラグインをダウンロード
WORKDIR /tmp/wp-plugins
RUN wget https://downloads.wordpress.org/plugin/advanced-custom-fields.4.4.11.zip
RUN wget https://downloads.wordpress.org/plugin/theme-check.20160523.1.zip
RUN wget https://downloads.wordpress.org/plugin/custom-post-type-ui.1.5.3.zip
RUN wget https://downloads.wordpress.org/plugin/mw-wp-form.3.2.1.zip
RUN wget https://downloads.wordpress.org/plugin/syntaxhighlighter.zip
RUN wget https://downloads.wordpress.org/plugin/google-sitemap-generator.4.0.8.zip

# Zip ファイルを解凍してインストール
RUN unzip './*.zip' -d /usr/src/wordpress/wp-content/plugins

# 不要になった一時ファイルを削除
RUN apt-get clean
RUN rm -rf /tmp/*

# サーバが読めるように wp-content 以下の所有者を変更
RUN chown -R www-data:www-data /usr/src/wordpress/wp-content

WORKDIR /var/www/html