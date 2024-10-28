# 使用 debian-slim 作为基础镜像
FROM debian:bookworm-slim


RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        tzdata \
        locales \
        fonts-noto-cjk \
        fonts-noto-cjk-extra \
        fonts-wqy-microhei \
        fonts-wqy-zenhei \
        xfonts-wqy \
    ; \
    # 设置时区
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime; \
    echo "Asia/Shanghai" > /etc/timezone; \
    # 设置语言
    localedef -i zh_CN -c -f UTF-8 -A /usr/share/locale/locale.alias zh_CN.UTF-8; \
    # 创建字体目录
    mkdir -p /usr/share/fonts/chinese; \
    # 复制字体（如果有自定义字体）
    # COPY ./fonts/* /usr/share/fonts/chinese/; \
    # 设置字体权限
    chmod 644 /usr/share/fonts/chinese/* || true; \
    # 更新字体缓存
    fc-cache -f -v; \
    # 清理缓存
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*

# 设置环境变量
ENV LANG zh_CN.utf8
ENV LANGUAGE zh_CN:zh
ENV LC_ALL zh_CN.utf8



# 验证设置
CMD ["bash"]