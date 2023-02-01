
 1. заходим в Active Directory
 
 2. Создаем подразделение в Demo.lab (office)
 
 3. Создаем пользователей в подразделение Office
 
3.1 При создании пользователя iwdm-admin зайти в свойства - член групп -  добавить "Domain Admins" - "Administrators"

 4. Заходим в веб панель (Логин Officer, Пароль xxXX1234)
 
 5. Заходим в управление - LDAP-серверы
 
 6. добавляем LDAP-сервер
 
 7. в имени пользвателя указываем ip админ машины
 
 8. в LDAP-сервере указываем ip админ машины
 
 9. в LDAP- запросе указываем  dc=demo,dc=lab
 
 10. в логине указываем ldap-user, пароль xxXX1234
 
 11. в следующем шаге заходим в управление - управление доступом
 
 12. В пользователях нажимаем создать пользователя 
 
 13. В редактированике пользователя указываем 
 
          Логин - iwtm-officer
          
          Статус - Активен
          
          Email - Любой (officer@demo.lab)
          
          Полное имя - iwtm-officer
          
          Роли - Администратор, Офицер безопасности
          
          Область видимости - Полный доступ, VIP
          
 14. Заходим в машину IWDM
 
 15. Настраиваем сеть
 
 16. подключаем машину к домену demo.lab (имя компьютера IWDM)
 
 17. перезагружаем машину и заходим в iwdm-admin
 
 18. Устанавливаем базу данных postgersql (При установке убираем Stack Builder)
 
 19. пока идет установка базы данных, настраиваем сеть agent (192.168.99.30) и gp (192.168.99.31)
 
 20. подключаем агента и гп к серверу demo.lab ( имя компьютера агента - W10-Agent, имя компьютера gp - W10-Agent-gp)
 
 21. в IWDM устанавливаем девайс монитор ( убираем галочку опубликовать сервер в Active Directory)
 
 Сервер БД - localhost
 
 Имя базы данных - iwdm
 
 Имя пользователя - postgres
 
 Пароль xxXX1234
 
в Учетной записи администратора сервера указываем имя пользователя officer, пароли xxXX1234

 22. Заходим в девайс монитор
 
 23. заходим в инструменты - настройки
 
 24. проверяем соединение
 
 25. далее заходим в интеграцию с Active Directory
 
 26. добавляем пользователи в директории office
 
 27. Добавляем компьютер в директории officer
 
 28. синхронизируем
 
 29. Далее начинаем работать с политиками
 
 30. в политиках создаем отдел 1 и отдел 2
 
 31. в группе компьютера создаем группу компьютеров по умолчанию
 
 Наименование Отдел1
 
 Политика отдел 1
 
 компьютеры в группе W10-Agent
 
 32. Создаем еще одну группу компьютеров отдел 2, и компьютеры гп
 
 33. в Политиках добавляем новое правило HTTPS монитор для отделов 1 и 2
 
 34. Далее заходим в инструменты -пользователи и консоли - добавить из AD - office - users - iwdm-admin
 
 35. в видит сотрудников, видит компьютеров, общие роли ставим все галочки
 
 36. в задачах добавляем задачу с наименованием 1, выбираем компьютер агента, запускаем задачу от demo.lab\iwdm-admin, пароль xxXX1234 
 (Количество запусков 10 каждую 1 минуту, в параметрах перезагрузки не ожидать, не уведомлять
 
 37. далее создаем пакет установки: инструменты - создать пакет установки
 
 38. перекидываем пакет который мы создали на машину Администратора
  
 39. в управлении груповой политики создаем новый объект групповой политики (install client)
 
 40. развертываем конфигурацию программ и в установке программ добавляем установщик инфовотч девайс монитор
