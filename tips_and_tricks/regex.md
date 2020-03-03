# Regex

## Remove all non numeric characters

- Signed integer : `/[^-+?][^\d].*/g`
  - 125.53 = 125
  - 125.53 = 125
- Unsigned integer : `/[^\d].*/g`
- Signed decimal : `/[^\d.-+]/g`
- Unsigned decimal : `/[^\d.]/g`
