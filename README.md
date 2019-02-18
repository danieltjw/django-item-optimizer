# Item Optimizer

https://iopt.herokuapp.com

App with a shared item database, user specific inventory of items and units, and an algorithm to find the find the best item allocation strategy.

---

### Workflow:

1. Add **Items**, and <b>Quantity</b> to your <b>Inventory</b> by searching the shared <b>Database</b> or adding a new Item
   <li>Add your <b>Units</b> and specifiy their total number of Item <b>Slots</b> </li>
   <li>Order your <b>Units</b> by drag-and-drop; those on top will have priority</li>
   <li>Run a <b>Report</b> to see the best <b>Item Combination</b> for each <b>Unit</b></li>
   <li>A non-greedy algorithm is used to find the best Items combinations per Unit </li>

---

### Technical:

- Reduce amount of Postgres's SQL queries with the use of QuerySet API's select_related() and prefetch_related().

  - Benchmarking using the Django Debug Toolbar and Locust load testing tool.

- Data Classes (Python 3.7) for faster access, compared to NamedTuple, with slots for reduced memory footprint.

- [Argon2](https://github.com/p-h-c/phc-winner-argon2) password hasher for better password security.

(Updating...)
