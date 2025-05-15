# Домашнее задание к занятию "`Ansible.Часть 2`" - `Виктория Лугинина`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

```yaml
---
- name: Download and extract Apache Kafka
  hosts: localhost
  become: yes
  tasks:
    - name: Create directory for Kafka
      ansible.builtin.file:
        path: /opt/kafka
        state: directory
        mode: '0755'

    - name: Download Kafka archive
      ansible.builtin.get_url:
        url: https://archive.apache.org/dist/kafka/3.7.0/kafka_2.13-3.7.0.tgz
        dest: /tmp/kafka_2.13-3.7.0.tgz
        mode: '0644'

    - name: Extract Kafka archive
      ansible.builtin.unarchive:
        src: /tmp/kafka_2.13-3.7.0.tgz
        dest: /opt/kafka
        remote_src: yes
        creates: /opt/kafka/kafka_2.13-3.7.0
```

```yaml
---
- name: Install and configure tuned
  hosts: localhost
  become: yes
  tasks:
    - name: Install tuned package
      ansible.builtin.apt:
        name: tuned
        state: present
        update_cache: yes

    - name: Ensure tuned service is started and enabled
      ansible.builtin.service:
        name: tuned
        state: started
        enabled: yes`
```

```yaml
---
- name: Customize motd with variable
  hosts: localhost
  become: yes
  vars:
    custom_motd: "Добро пожаловать в мой сервер! - Виктория Лугинина"
  tasks:
    - name: Update motd file
      ansible.builtin.copy:
        content: "{{ custom_motd }}"
        dest: /etc/motd
        mode: '0644'
```

![вывод_playbook1-download.png](https://github.com/victorialugi/ansible2-hw/blob/main/%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4_playbook1-download.png)
![вывод_playbook2-tuned.png](https://github.com/victorialugi/ansible2-hw/blob/main/%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4_playbook2-tuned.png)
![вывод_playbook3-motd.png](https://github.com/victorialugi/ansible2-hw/blob/main/%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4_playbook3-motd.png)`

---

### Задание 2

```yaml
---
- name: Customize motd with IP, hostname, and greeting
  hosts: localhost
  become: yes
  vars:
    greeting: "Хорошего дня, системный администратор!"
  tasks:
    - name: Update motd file with IP, hostname, and greeting
      ansible.builtin.copy:
        content: |
          IP Address: {{ ansible_facts['default_ipv4']['address'] }}
          Hostname: {{ ansible_facts['hostname'] }}
          {{ greeting }}
        dest: /etc/motd
        mode: '0644'
```

`![вывод_задание_2.png](https://github.com/victorialugi/ansible2-hw/blob/main/%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4_%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5_2.png)`


---

### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
