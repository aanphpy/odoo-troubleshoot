# Uninstall Module From CLI

Run from Terminal:

```sh
./odoo-bin shell -c nama-config.conf -d namadb
```

Run from python console:

```python
self.env['ir.module.module'].search([('name', '=', 'crm')]).button_immediate_uninstall()
```
