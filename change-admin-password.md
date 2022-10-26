# Merubah Password Admin Jika Lupa

## Lewat Shell

```sh
$ ./odoo-bin shell -c nama-odoo-config.conf -d nama_db
```
```python
>>> admin = self.env['res.users'].browse(2)
>>> admin.write({'password': 'passwordbaru'})
```

# Lewat Database

```sh
$ python3
```
```python
>>> from passlib.context import CryptContext
>>> print(CryptContext(['pbkdf2_sha512']).encrypt('passwordbaru'))
```
Copy string enkripsi yang dihasilkan, misal dari contoh:
```sh
$pbkdf2-sha512$25000$T0lpDeE8R2gt5TxHKAWgVA$J9khc9k9Bqk6np4kWHAP8CRWAMvdGootkTw4kIZFTxSFTo.5JX1.Xl7qtff5cMQKfFjFnZ7arXn1KzDYM8GnUg
```
Dari `psql`:
```sql
update res_users set password='$pbkdf2-sha512$25000$T0lpDeE8R2gt5TxHKAWgVA$J9khc9k9Bqk6np4kWHAP8CRWAMvdGootkTw4kIZFTxSFTo.5JX1.Xl7qtff5cMQKfFjFnZ7arXn1KzDYM8GnUg' where id=2;
```
