# 使用 debian-slim 作为基础镜像
FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y locales tzdata && rm -rf /var/lib/apt/lists/* \
	&& localedef -i zh_CN -c -f UTF-8 -A /usr/share/locale/locale.alias zh_CN.UTF-8
ENV LANG zh_CN.utf8



# 验证设置
CMD ["bash"]