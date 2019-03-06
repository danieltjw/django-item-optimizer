# Item Optimizer

Google App Engine Deployment: https://item-opt.appspot.com

AWS Lambda "Serverless" Deployment: https://pks3imvspa.execute-api.ca-central-1.amazonaws.com/dev

Heroku Deployment: https://iopt.herokuapp.com

App with a shared item database, user specific inventory of items and units, and an algorithm to find the find the best item allocation strategy.

---

## Highlights:

### Auth0 Integrations

In this deployment: https://item-opt.appspot.com

[Auth0](https://auth0.com) authentication backend optional provides:

- Mitigates against brute force attacks
- Multi-factor authentication
- Single Sign-On / Active Directory
- Existing database user migration

---

### Autocomplete

Django 2 comes with autocomplete search out of the box!

![](img/item-autocomplete.gif "Item Autocomplete")

---

### Mobile compatible

![](img/Mobile-Auth0-Login.png "Mobile Auth0 Login") ![](img/Mobile-Main.png "Mobile Main")

---

### Database Filtering

This filters a Unit's Equipped Items by the relationship:

**Unit** <-ManyToMany-> **Item-Instance** <-FK-> **Item** <-ManyToMany-> **Class**

![](img/unit-item-filter.gif "Unit Item Filter")

---

### Item Private Toggle

Items added to the shared **Item Database** have an option to be made **Private** which renders the item only viewable by the owner. This gives users the option to not list their items in the database. Furthermore, admins can use it to archive outdated items and declutter the database view all while maintaining backwards compatibility.

![](img/item-private.png "Item Private Mode")

---

## Workflow:

1. Add **Items**, and <b>Quantity</b>, to your <b>Inventory</b> by searching the shared <b>Database</b> or adding a new Item
   <li>Add your <b>Units</b> and specify their total number of Item <b>Slots</b> </li>
   <li>Order your <b>Units</b> by drag-and-drop; those on top will have priority</li>
   <li>Run a <b>Report</b> to see the best <b>Item Combination</b> for each <b>Unit</b></li>
   <li>A non-greedy algorithm is used to find the best Items combinations per Unit </li>

---

## Technical:

- Reduce amount of Postgres's SQL queries with the use of QuerySet API's select_related() and prefetch_related()

  - Benchmarking using the Django Debug Toolbar and Locust load testing tool

- [Data Classes](https://www.youtube.com/watch?v=T-TwcmT6Rcw) (Python 3.7) for faster access, compared to NamedTuple (3.7), with slots for reduced memory footprint

- [Argon2](https://github.com/p-h-c/phc-winner-argon2) password hasher, over the default PBKDF2, for better password security

- Customising the user interface and workflow design by overwriting and extending Forms, Templates, TemplateResponse, list view default sort order

- AWS Lambda serverless deployment for scalability and cost-effectiveness (non-uniform utilization)

(Updating...)
