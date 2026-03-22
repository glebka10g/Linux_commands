### Пример использования в Ansible

```yaml
### Пример использования Handlers
tasks:
  - name: Update nginx config
    template:
      src: nginx.conf.j2
      dest: /etc/nginx/nginx.conf
    notify: Restart nginx

handlers:
  - name: Restart nginx
    service:
      name: nginx
      state: restarted

### Пример использования Сonditionals

```yaml
- name: Install nginx on Debian
  apt:
    name: nginx
    state: present
  when: ansible_os_family == "Debian" (в этом случае проверяется установленный ли Debian?)

### COPY
```yaml
- name: Copy with permissions
  hosts: all
  become: yes

  tasks:
    - name: Copy file with mode
      copy:
        src: test.txt
        dest: /tmp/test.txt
        owner: root
        group: root
        mode: '0644'
