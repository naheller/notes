create user:
- useradd -m nate
  - "-m" make a home directory
- passwd nate

add user to wheel group:
- usermod -a -G wheel nate
  - "-a" append group (instead of replace all groups with just wheel)
  - "-G" group

how to give wheel members sudo ability?

