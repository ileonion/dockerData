FROM nginx:latest

# 更改配置文件（优化参数，更改连接方式为socket，添加VHOST配置目录）
ADD configFiles/nginx.conf /etc/nginx/nginx.conf
ADD configFiles/phpfpm_56.conf /etc/nginx/conf.d/phpfpm_56.conf
ADD configFiles/default.conf /etc/nginx/vhost/default.conf

# 删除conf.d/default.conf文件
RUN rm -f /etc/nginx/conf.d/default.conf
