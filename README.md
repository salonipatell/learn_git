# learn_git
Latest version =5.24.1
currently i am working =5.23

what is frappe bench ?
Frappe Bench is a command-line tool to manage multiple Frappe sites, apps, environments, and processes in a consistent setup.
----------------------------------------------------------------------------------------------------------------------------------------
import requests

url = "https://site-b.com/api/resource/Item"
headers = {
    "Authorization": "token YOUR_API_KEY:YOUR_API_SECRET"
}
response = requests.get(url, headers=headers)
data = response.json()
-------------------------------------------------------------------------------------------------------------------

import frappe

# Save current site
current_site = frappe.local.site

# Switch to site-b
frappe.init(site='site-b')
frappe.connect()
frappe.local.login_manager = frappe.auth.LoginManager()
frappe.set_user('Administrator')

# Do something on site-b
doc = frappe.get_doc({
    'doctype': 'ToDo',
    'description': 'Created from Site A'
})
doc.insert()
frappe.db.commit()

# Restore to original site
frappe.destroy()
frappe.init(site=current_site)
frappe.connect()

----------------------------------------------------------------------------------------------------
https://frappecloud.com/pricing
