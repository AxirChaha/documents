# Class User

```php
<?php

namespace app;

class User
{
    public function __construct(
        public string $name,
        public string $email,
        public string $password = '',
        public string $group = 'user'
    )
    {
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function getEmail(): string
    {
        return $this->email;
    }
    public function getPassword(): string
    {
        return $this->password;
    }
    public function getGroup(): string
    {
        return $this->group;
    }

    public function getUser(): array
    {
        return [
            "name" => $this->name,
            "email" => $this->email,
            "password" => $this->password,
            "group" => $this->group
        ];
    }

    public function jsonUser(): false|string
    {
        return json_encode($this->getUser());
    }

    public function setGroup(string $group): void
    {
        $this->group = $group;
    }

    public function setPassword(string $password): void
    {
        $this->password = password_hash($password, PASSWORD_DEFAULT);
    }
}
```
