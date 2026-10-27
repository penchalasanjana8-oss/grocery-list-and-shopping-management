# grocery-list-and-shopping-management
Keep track of items you already have at home so you don't buy duplicates.

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FreshList | Grocery Shopping Manager</title>

<style>
:root {
  --green: #247A4B;
  --dark-green: #176441;
  --mint: #E7F5E9;
  --bg: #F7F8F4;
  --white: #FFFFFF;
  --text: #252D27;
  --muted: #738076;
  --border: #E1E9E1;
  --orange: #E9A23B;
  --shadow: 0 4px 15px rgba(30, 70, 40, 0.05);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background: var(--bg);
  color: var(--text);
}

button, input, select {
  font: inherit;
}

button {
  cursor: pointer;
}

button:focus-visible,
input:focus-visible,
select:focus-visible {
  outline: 2px solid var(--green);
  outline-offset: 2px;
}

/* HEADER */

.header {
  height: 72px;
  background: white;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 28px;
  gap: 25px;
  position: sticky;
  top: 0;
  z-index: 10;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--green);
  min-width: 205px;
}

.logo-icon {
  font-size: 32px;
}

.logo h2 {
  font-size: 24px;
}

.logo small {
  display: block;
  color: var(--muted);
  font-size: 10px;
  margin-top: 3px;
}

.search {
  flex: 1;
  max-width: 580px;
}

.search input {
  width: 100%;
  padding: 12px 17px;
  border: 1px solid var(--border);
  border-radius: 25px;
  background: #FAFCF9;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  background: var(--mint);
  color: var(--green);
  display: grid;
  place-items: center;
  font-weight: bold;
}

.profile small {
  display: block;
  margin-top: 4px;
  color: var(--muted);
}

/* SIDEBAR */

.sidebar {
  position: fixed;
  top: 72px;
  bottom: 0;
  width: 245px;
  padding: 25px 15px;
  background: #FBFCF9;
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
}

.sidebar button {
  display: flex;
  gap: 13px;
  align-items: center;
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 9px;
  background: transparent;
  text-align: left;
  color: #435248;
  margin-bottom: 6px;
  font-size: 14px;
}

.sidebar button:hover {
  background: var(--mint);
}

.sidebar button.active {
  background: var(--green);
  color: white;
}

.sidebar-tip {
  margin-top: auto;
  padding: 18px;
  background: var(--mint);
  border-radius: 12px;
  line-height: 1.6;
  color: var(--dark-green);
}

.sidebar-tip p {
  margin-top: 10px;
  font-size: 13px;
}

/* MAIN */

.main {
  margin-left: 245px;
  padding: 28px;
}

.welcome {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  margin-bottom: 25px;
}

.welcome h1 {
  font-size: 27px;
  margin-bottom: 9px;
}

.welcome p {
  color: var(--muted);
  font-size: 14px;
}

.date {
  color: var(--green);
  font-size: 13px;
  white-space: nowrap;
}

/* SUMMARY CARDS */

.stats {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 16px;
  margin-bottom: 20px;
}

.card {
  background: white;
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 20px;
  box-shadow: var(--shadow);
}

.stat-icon {
  width: 42px;
  height: 42px;
  display: grid;
  place-items: center;
  border-radius: 11px;
  background: var(--mint);
  font-size: 22px;
  margin-bottom: 15px;
}

.stat-icon.orange {
  background: #FFF0D9;
}

.stat-label {
  font-size: 13px;
  color: var(--muted);
  margin-bottom: 10px;
}

.stat-value {
  font-size: 27px;
  font-weight: bold;
  margin-bottom: 7px;
  overflow-wrap: anywhere;
}

.stat-note {
  font-size: 11px;
  color: var(--muted);
}

/* PROGRESS */

.progress-card {
  margin-bottom: 20px;
}

.progress-header {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 15px;
  font-weight: bold;
}

.progress-header span:last-child {
  color: var(--green);
}

.progress-track {
  width: 100%;
  height: 10px;
  background: #E8EEE8;
  border-radius: 20px;
  overflow: hidden;
}

.progress-bar {
  height: 100%;
  width: 0;
  background: var(--green);
  border-radius: 20px;
  transition: width 0.25s;
}

/* DASHBOARD GRID */

.dashboard-grid {
  display: grid;
  grid-template-columns: minmax(0, 1.6fr) minmax(300px, 1fr);
  gap: 20px;
  align-items: start;
}

.panel {
  background: white;
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 20px;
  box-shadow: var(--shadow);
  margin-bottom: 18px;
  min-width: 0;
}

.panel-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 18px;
}

.panel-header h2,
.panel h2 {
  font-size: 17px;
}

select,
input {
  color: var(--text);
}

.panel select {
  padding: 9px;
  border: 1px solid var(--border);
  border-radius: 7px;
  background: white;
  max-width: 100%;
}

/* SHOPPING LIST */

.category-heading {
  padding: 12px;
  margin-top: 12px;
  background: #EDF7EF;
  border-radius: 8px;
  color: var(--dark-green);
  font-weight: bold;
  font-size: 13px;
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.grocery-row {
  display: grid;
  grid-template-columns: 22px 28px minmax(60px, 1fr) auto;
  gap: 10px;
  align-items: center;
  padding: 13px 5px;
  border-bottom: 1px solid #EEF1ED;
}

.grocery-row input {
  width: 17px;
  height: 17px;
  accent-color: var(--green);
}

.food-icon {
  font-size: 22px;
}

.item-name {
  font-size: 13px;
  overflow-wrap: anywhere;
}

.item-name.done {
  text-decoration: line-through;
  color: #98A19A;
}

.item-price {
  font-weight: bold;
  font-size: 12px;
  white-space: nowrap;
}

.item-details {
  display: block;
  font-size: 11px;
  color: var(--muted);
  margin-top: 5px;
}

.item-status {
  font-size: 10px;
  padding: 5px 8px;
  border-radius: 20px;
  margin-top: 5px;
  display: inline-block;
}

.status-pending {
  color: #A86505;
  background: #FFF0D9;
}

.status-done {
  color: var(--green);
  background: var(--mint);
}

.delete-btn {
  border: none;
  background: transparent;
  color: #D65B4A;
  font-size: 17px;
  padding: 3px;
}

.list-actions {
  display: flex;
  gap: 10px;
  margin-top: 18px;
  flex-wrap: wrap;
}

/* BUTTONS */

.btn {
  border: none;
  border-radius: 7px;
  padding: 11px 15px;
  font-size: 12px;
  font-weight: bold;
}

.btn-primary {
  background: var(--green);
  color: white;
}

.btn-primary:hover {
  background: var(--dark-green);
}

.btn-outline {
  border: 1px solid var(--border);
  color: var(--green);
  background: white;
}

.btn-outline:hover {
  background: var(--mint);
}

/* QUICK ADD */

.form-group {
  margin-bottom: 13px;
}

.form-group label {
  display: block;
  font-size: 12px;
  font-weight: bold;
  margin-bottom: 7px;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 12px;
  border: 1px solid var(--border);
  border-radius: 7px;
  background: white;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.full-button {
  width: 100%;
}

.message {
  font-size: 12px;
  color: var(--green);
  margin-top: 10px;
}

/* BUDGET */

.budget-content {
  display: flex;
  align-items: center;
  justify-content: space-around;
  gap: 20px;
  flex-wrap: wrap;
}

.donut {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  position: relative;
  background: conic-gradient(var(--green) 0%, #E8EEE8 0%);
  flex-shrink: 0;
}

.donut::before {
  content: "";
  position: absolute;
  inset: 19px;
  background: white;
  border-radius: 50%;
}

.donut-inner {
  position: relative;
  text-align: center;
  z-index: 1;
}

.donut-inner strong {
  display: block;
  font-size: 17px;
}

.donut-inner small {
  display: block;
  color: var(--muted);
  margin-top: 5px;
  font-size: 10px;
}

.legend {
  flex: 1;
  min-width: 135px;
}

.legend-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 14px 0;
  font-size: 11px;
}

.legend-row strong {
  margin-left: auto;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
}

.dot-green {
  background: var(--green);
}

.dot-orange {
  background: var(--orange);
}

.dot-gray {
  background: #C6CEC7;
}

/* SECONDARY PAGES */

.page-view {
  display: none;
}

.page-view.active {
  display: block;
}

.secondary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
  gap: 15px;
}

.category-tile {
  background: white;
  border: 1px solid var(--border);
  padding: 20px;
  border-radius: 10px;
}

.category-tile h3 {
  font-size: 14px;
  margin: 12px 0;
}

.category-tile p {
  color: var(--muted);
  font-size: 12px;
}

.history-row,
.saved-row {
  padding: 15px 0;
  border-bottom: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
}

.history-row small,
.saved-row small {
  display: block;
  color: var(--muted);
  margin-top: 6px;
}

.empty-state {
  text-align: center;
  padding: 35px 10px;
  color: var(--muted);
  font-size: 13px;
}

.empty-state h3 {
  color: var(--text);
  margin-bottom: 8px;
}

/* TIP */

.tip {
  background: var(--mint);
  padding: 18px;
  border-radius: 10px;
  color: var(--dark-green);
  line-height: 1.7;
  font-size: 13px;
}

.tip strong {
  display: block;
  margin-bottom: 5px;
}

/* FOOTER AND TOAST */

footer {
  padding: 25px 10px;
  text-align: center;
  color: var(--muted);
  font-size: 11px;
}

.toast {
  position: fixed;
  bottom: 22px;
  right: 22px;
  max-width: calc(100vw - 44px);
  background: #183E2A;
  color: white;
  padding: 14px 20px;
  border-radius: 9px;
  opacity: 0;
  transform: translateY(10px);
  transition: 0.2s;
  pointer-events: none;
  z-index: 100;
}

.toast.show {
  opacity: 1;
  transform: translateY(0);
}

/* RESPONSIVE */

@media (max-width: 1150px) {
  .sidebar {
    width: 210px;
  }

  .main {
    margin-left: 210px;
    padding: 20px;
  }

  .stats {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .dashboard-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 700px) {
  .header {
    height: 65px;
    padding: 0 12px;
    gap: 12px;
  }

  .logo {
    min-width: 0;
  }

  .logo h2 {
    font-size: 19px;
  }

  .logo small,
  .profile-info,
  .profile-arrow {
    display: none;
  }

  .logo-icon {
    font-size: 25px;
  }

  .search input {
    padding: 10px;
    font-size: 11px;
  }

  .sidebar {
    top: 65px;
    width: 57px;
    padding: 12px 5px;
  }

  .sidebar button {
    justify-content: center;
    padding: 14px 3px;
    font-size: 0;
  }

  .sidebar button span {
    font-size: 20px;
  }

  .sidebar-tip {
    display: none;
  }

  .main {
    margin-left: 57px;
    padding: 18px 10px;
  }

  .welcome h1 {
    font-size: 20px;
  }

  .welcome p {
    font-size: 12px;
    line-height: 1.5;
  }

  .date {
    display: none;
  }

  .stats {
    gap: 9px;
  }

  .card {
    padding: 13px;
  }

  .stat-value {
    font-size: 21px;
  }

  .stat-label {
    font-size: 11px;
  }

  .stat-note {
    font-size: 10px;
  }

  .stat-icon {
    width: 35px;
    height: 35px;
  }

  .panel {
    padding: 13px;
  }

  .grocery-row {
    grid-template-columns: 20px 24px minmax(40px, 1fr) auto;
    gap: 7px;
  }

  .item-name {
    font-size: 12px;
  }

  .item-price {
    font-size: 11px;
  }

  .budget-content {
    gap: 15px;
  }

  .donut {
    width: 120px;
    height: 120px;
  }

  .donut::before {
    inset: 16px;
  }

  .list-actions .btn {
    flex: 1;
  }
}
</style>
</head>

<body>

<header class="header">
  <div class="logo">
    <span class="logo-icon">🌿</span>
    <div>
      <h2>FreshList</h2>
      <small>Better Food · Better Life</small>
    </div>
  </div>

  <div class="search">
    <input type="search" id="searchInput"
      placeholder="Search grocery items...">
  </div>

  <div class="profile">
    <div class="avatar">F</div>
    <div class="profile-info">
      <strong>FreshList User</strong>
      <small>Smart Shopper</small>
    </div>
    <span class="profile-arrow">⌄</span>
  </div>
</header>

<aside class="sidebar">
  <nav>
    <button class="active" data-page="dashboard">
      <span>⌂</span> Dashboard
    </button>
    <button data-page="lists">
      <span>☷</span> My Shopping Lists
    </button>
    <button data-page="categories">
      <span>▦</span> Categories
    </button>
    <button data-page="budget">
      <span>₹</span> Budget & Expenses
    </button>
    <button data-page="recurring">
      <span>⟳</span> Saved & Recurring Lists
    </button>
    <button data-page="history">
      <span>◷</span> Shopping History
    </button>
    <button data-page="settings">
      <span>⚙</span> Settings
    </button>
  </nav>

  <div class="sidebar-tip">
    <strong>🌱 Shop Smart!</strong>
    <p>Plan your groceries, control your budget and reduce food waste.</p>
  </div>
</aside>

<main class="main">

  <div class="welcome">
    <div>
      <h1 id="welcomeTitle">Hello, Shopper! 👋</h1>
      <p id="welcomeSubtitle">
        Let's make your grocery shopping simple and smart.
      </p>
    </div>
    <div class="date" id="todayDate"></div>
  </div>

  <!-- DASHBOARD -->

  <section class="page-view active" id="dashboard">

    <div class="stats">
      <article class="card">
        <div class="stat-icon">🛒</div>
        <p class="stat-label">Items to Buy</p>
        <h2 class="stat-value" id="itemsToBuy">0</h2>
        <p class="stat-note" id="itemsCaption">Items remaining</p>
      </article>

      <article class="card">
        <div class="stat-icon orange">₹</div>
        <p class="stat-label">Estimated Cost</p>
        <h2 class="stat-value" id="estimatedCost">₹0</h2>
        <p class="stat-note">Planned shopping expense</p>
      </article>

      <article class="card">
        <div class="stat-icon">✓</div>
        <p class="stat-label">Items Purchased</p>
        <h2 class="stat-value" id="itemsPurchased">0</h2>
        <p class="stat-note" id="purchaseCaption">0% complete</p>
      </article>

      <article class="card">
        <div class="stat-icon orange">▱</div>
        <p class="stat-label">Budget Remaining</p>
        <h2 class="stat-value" id="budgetRemaining">₹0</h2>
        <p class="stat-note" id="budgetCaption">Available budget</p>
      </article>
    </div>

    <section class="card progress-card">
      <div class="progress-header">
        <span>🛒 Shopping Progress</span>
        <span id="progressText">0 / 0 items · 0%</span>
      </div>
      <div class="progress-track">
        <div class="progress-bar" id="progressBar"></div>
      </div>
    </section>

    <div class="dashboard-grid">

      <!-- SHOPPING LIST -->

      <section class="panel">
        <div class="panel-header">
          <h2>🧺 My Shopping List</h2>

          <select id="listSelect" aria-label="Select shopping list">
            <option value="weekly">Weekly Grocery</option>
            <option value="party">Party Essentials</option>
          </select>
        </div>

        <div id="shoppingItems"></div>

        <div class="list-actions">
          <button class="btn btn-outline" id="clearPurchased">
            Clear Purchased
          </button>
          <button class="btn btn-primary" id="finishShopping">
            Finish Shopping ✓
          </button>
        </div>
      </section>

      <div>

        <!-- ADD ITEM -->

        <section class="panel">
          <div class="panel-header">
            <h2>＋ Quick Add Item</h2>
          </div>

          <form id="itemForm">

            <div class="form-group">
              <label for="itemName">Item Name</label>
              <input id="itemName" type="text"
                placeholder="e.g. Fresh Apples" maxlength="80" required>
            </div>

            <div class="form-row">
              <div class="form-group">
                <label for="itemQty">Quantity</label>
                <input id="itemQty" type="number"
                  min="0.01" step="any" value="1" required>
              </div>

              <div class="form-group">
                <label for="itemUnit">Unit</label>
                <select id="itemUnit">
                  <option>pcs</option>
                  <option>kg</option>
                  <option>g</option>
                  <option>litres</option>
                  <option>ml</option>
                  <option>packets</option>
                  <option>dozens</option>
                </select>
              </div>
            </div>

            <div class="form-group">
              <label for="itemCategory">Category</label>
              <select id="itemCategory">
                <option>Fruits & Vegetables</option>
                <option>Dairy & Eggs</option>
                <option>Grains & Staples</option>
                <option>Bakery</option>
                <option>Snacks & Beverages</option>
                <option>Meat & Seafood</option>
                <option>Household</option>
                <option>Other</option>
              </select>
            </div>

            <div class="form-group">
              <label for="itemPrice">Price per Unit (₹)</label>
              <input id="itemPrice" type="number"
                min="0" step="0.01" placeholder="Enter estimated price">
            </div>

            <button class="btn btn-primary full-button" type="submit">
              ＋ Add to Shopping List
            </button>

            <p class="message" id="formMessage"></p>
          </form>
        </section>

        <!-- BUDGET -->

        <section class="panel">
          <div class="panel-header">
            <h2>▥ Budget Overview</h2>
          </div>

          <div class="budget-content">
            <div class="donut" id="budgetDonut">
              <div class="donut-inner">
                <strong id="donutSpent">₹0</strong>
                <small>Actual spent</small>
              </div>
            </div>

            <div class="legend">
              <div class="legend-row">
                <span class="dot dot-green"></span>
                <span>Actual Spent</span>
                <strong id="actualSpent">₹0</strong>
              </div>

              <div class="legend-row">
                <span class="dot dot-orange"></span>
                <span>Estimated</span>
                <strong id="legendEstimated">₹0</strong>
              </div>

              <div class="legend-row">
                <span class="dot dot-gray"></span>
                <span>Remaining</span>
                <strong id="legendRemaining">₹0</strong>
              </div>
            </div>
          </div>

          <div class="form-group" style="margin-top:20px">
            <label for="budgetInput">Shopping Budget (₹)</label>
            <input id="budgetInput" type="number" min="0"
              step="1" value="4000">
          </div>

          <button class="btn btn-outline full-button" id="saveBudget">
            Update Budget
          </button>
        </section>

        <div class="tip">
          <strong>🌿 Smart Shopping Tip</strong>
          Buy seasonal fruits and vegetables, compare prices, and make a list
          before visiting the store to reduce unnecessary spending.
        </div>

      </div>
    </div>
  </section>

  <!-- SHOPPING LISTS PAGE -->

  <section class="page-view" id="lists">
    <section class="panel">
      <h2>My Shopping Lists</h2>
      <p style="margin:12px 0 20px;color:var(--muted)">
        Manage your shopping lists and switch between them.
      </p>

      <div class="category-tile">
        <h3>🛒 Weekly Grocery</h3>
        <p>Regular household shopping.</p>
        <br>
        <button class="btn btn-primary" data-open-list="weekly">
          Open List
        </button>
      </div>

      <br>

      <div class="category-tile">
        <h3>🎉 Party Essentials</h3>
        <p>Snacks, drinks and party supplies.</p>
        <br>
        <button class="btn btn-primary" data-open-list="party">
          Open List
        </button>
      </div>

      <br>

      <form id="newListForm">
        <div class="form-group">
          <label for="newListName">Create Another Shopping List</label>
          <input id="newListName" placeholder="e.g. Monthly Shopping"
            maxlength="60" required>
        </div>
        <button class="btn btn-primary" type="submit">
          ＋ Create List
        </button>
      </form>
    </section>
  </section>

  <!-- CATEGORIES PAGE -->

  <section class="page-view" id="categories">
    <section class="panel">
      <h2>Grocery Categories</h2>
      <p style="margin:10px 0 20px;color:var(--muted)">
        Explore categories and the items in your current shopping list.
      </p>
      <div class="secondary-grid" id="categoryGrid"></div>
    </section>
  </section>

  <!-- BUDGET PAGE -->

  <section class="page-view" id="budget">
    <section class="panel">
      <h2>Budget & Expenses</h2>
      <p style="margin:10px 0 20px;color:var(--muted)">
        Track your planned grocery costs and spending.
      </p>
      <div class="secondary-grid" id="budgetDetails"></div>
      <br>
      <button class="btn btn-primary" id="budgetPageButton">
        Update Budget
      </button>
    </section>
  </section>

  <!-- RECURRING LISTS PAGE -->

  <section class="page-view" id="recurring">
    <section class="panel">
      <h2>Saved & Recurring Lists</h2>
      <p style="margin:10px 0 20px;color:var(--muted)">
        Save frequently used lists and create new shopping lists from them.
      </p>
      <div id="recurringItems"></div>
      <br>
      <button class="btn btn-primary" id="saveRecurring">
        ＋ Save Current List as Template
      </button>
    </section>
  </section>

  <!-- HISTORY PAGE -->

  <section class="page-view" id="history">
    <section class="panel">
      <h2>Shopping History</h2>
      <p style="margin:10px 0 20px;color:var(--muted)">
        Review your previously completed shopping trips.
      </p>
      <div id="historyItems"></div>
    </section>
  </section>

  <!-- SETTINGS PAGE -->

  <section class="page-view" id="settings">
    <section class="panel">
      <h2>Settings</h2>
      <p style="margin:10px 0 20px;color:var(--muted)">
        Manage your local FreshList application data.
      </p>

      <div class="category-tile">
        <h3>💰 Currency</h3>
        <p>Indian Rupee (INR)</p>
      </div>

      <br>

      <div class="category-tile">
        <h3>💾 Data Storage</h3>
        <p>
          This demo stores your shopping data in your browser.
          It does not use a remote server.
        </p>
      </div>

      <br>

      <button class="btn btn-outline" id="resetData">
        Reset Demo Data
      </button>
    </section>
  </section>

  <footer>
    FreshList © <span id="year"></span> · Plan smarter, shop better.
  </footer>

</main>

<div class="toast" id="toast" role="status"></div>

<script>
/* FRESHLIST GROCERY SHOPPING MANAGER */

const $ = id => document.getElementById(id);

const CATEGORIES = [
  "Fruits & Vegetables",
  "Dairy & Eggs",
  "Grains & Staples",
  "Bakery",
  "Snacks & Beverages",
  "Meat & Seafood",
  "Household",
  "Other"
];

const CATEGORY_ICONS = {
  "Fruits & Vegetables": "🥦",
  "Dairy & Eggs": "🥛",
  "Grains & Staples": "🌾",
  "Bakery": "🥖",
  "Snacks & Beverages": "🥫",
  "Meat & Seafood": "🍗",
  "Household": "🧽",
  "Other": "🛍️"
};

const DEFAULT_LISTS = {
  weekly: {
    name: "Weekly Grocery",
    budget: 4000,
    items: [
      {id:1,name:"Tomatoes",qty:1,unit:"kg",category:"Fruits & Vegetables",price:40,purchased:true,actualPrice:40},
      {id:2,name:"Bananas",qty:6,unit:"pcs",category:"Fruits & Vegetables",price:10,purchased:true,actualPrice:10},
      {id:3,name:"Apples",qty:1,unit:"kg",category:"Fruits & Vegetables",price:120,purchased:false,actualPrice:null},
      {id:4,name:"Spinach",qty:0.5,unit:"kg",category:"Fruits & Vegetables",price:50,purchased:false,actualPrice:null},
      {id:5,name:"Milk",qty:2,unit:"litres",category:"Dairy & Eggs",price:60,purchased:true,actualPrice:60},
      {id:6,name:"Eggs",qty:12,unit:"pcs",category:"Dairy & Eggs",price:6,purchased:false,actualPrice:null},
      {id:7,name:"Paneer",qty:0.25,unit:"kg",category:"Dairy & Eggs",price:140,purchased:false,actualPrice:null},
      {id:8,name:"Rice",qty:5,unit:"kg",category:"Grains & Staples",price:60,purchased:false,actualPrice:null},
      {id:9,name:"Wheat Flour",qty:2,unit:"kg",category:"Grains & Staples",price:60,purchased:false,actualPrice:null},
      {id:10,name:"Moong Dal",qty:1,unit:"kg",category:"Grains & Staples",price:110,purchased:false,actualPrice:null},
      {id:11,name:"Sugar",qty:1,unit:"kg",category:"Grains & Staples",price:45,purchased:false,actualPrice:null}
    ]
  },

  party: {
    name: "Party Essentials",
    budget: 2500,
    items: [
      {id:12,name:"Chips",qty:4,unit:"packets",category:"Snacks & Beverages",price:30,purchased:false,actualPrice:null},
      {id:13,name:"Juice",qty:3,unit:"litres",category:"Snacks & Beverages",price:100,purchased:false,actualPrice:null},
      {id:14,name:"Bread",qty:2,unit:"pcs",category:"Bakery",price:40,purchased:false,actualPrice:null}
    ]
  }
};

function clone(value) {
  return JSON.parse(JSON.stringify(value));
}

function loadJSON(key, fallback) {
  try {
    const value = localStorage.getItem(key);
    return value ? JSON.parse(value) : clone(fallback);
  } catch {
    return clone(fallback);
  }
}

let lists = loadJSON("freshlist-lists", DEFAULT_LISTS);
let history = loadJSON("freshlist-history", []);
let recurring = loadJSON("freshlist-recurring", []);
let currentList = "weekly";
let currentPage = "dashboard";
let searchQuery = "";

function saveData() {
  localStorage.setItem("freshlist-lists", JSON.stringify(lists));
  localStorage.setItem("freshlist-history", JSON.stringify(history));
  localStorage.setItem("freshlist-recurring", JSON.stringify(recurring));
}

function money(value) {
  return new Intl.NumberFormat("en-IN", {
    style: "currency",
    currency: "INR",
    maximumFractionDigits: 2
  }).format(Number(value) || 0);
}

function escapeHTML(value) {
  return String(value).replace(/[&<>"']/g, character => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#39;"
  })[character]);
}

function activeList() {
  return lists[currentList];
}

function estimatedTotal(items = activeList().items) {
  return items.reduce((sum, item) =>
    sum + item.qty * (Number(item.price) || 0), 0);
}

function actualTotal(items = activeList().items) {
  return items.reduce((sum, item) => {
    if (!item.purchased) return sum;

    const price = item.actualPrice == null
      ? item.price
      : item.actualPrice;

    return sum + item.qty * (Number(price) || 0);
  }, 0);
}

function toast(message) {
  const el = $("toast");
  el.textContent = message;
  el.classList.add("show");

  clearTimeout(toast.timer);
  toast.timer = setTimeout(() => el.classList.remove("show"), 2500);
}

function getEmoji(item) {
  const name = item.name.toLowerCase();

  if (name.includes("banana")) return "🍌";
  if (name.includes("apple")) return "🍎";
  if (name.includes("tomato")) return "🍅";
  if (name.includes("milk")) return "🥛";
  if (name.includes("egg")) return "🥚";
  if (name.includes("bread")) return "🍞";
  if (name.includes("rice")) return "🍚";
  if (name.includes("spinach")) return "🥬";
  if (name.includes("paneer")) return "🧀";
  if (name.includes("chicken")) return "🍗";

  return CATEGORY_ICONS[item.category] || "🛍️";
}

/* DASHBOARD RENDERING */

function renderDashboard() {
  const items = activeList().items;
  const purchased = items.filter(item => item.purchased).length;
  const pending = items.length - purchased;
  const estimated = estimatedTotal();
  const actual = actualTotal();
  const budget = Number(activeList().budget) || 0;
  const remaining = budget - actual;
  const percent = items.length
    ? Math.round(purchased / items.length * 100)
    : 0;

  $("itemsToBuy").textContent = pending;
  $("itemsCaption").textContent = `${items.length} total items`;
  $("estimatedCost").textContent = money(estimated);
  $("itemsPurchased").textContent = purchased;
  $("purchaseCaption").textContent = `${percent}% complete`;
  $("budgetRemaining").textContent = money(remaining);
  $("budgetCaption").textContent = `of ${money(budget)} budget`;

  $("progressText").textContent =
    `${purchased} / ${items.length} items · ${percent}%`;

  $("progressBar").style.width = `${percent}%`;
  $("budgetInput").value = budget;

  $("donutSpent").textContent = money(actual);
  $("actualSpent").textContent = money(actual);
  $("legendEstimated").textContent = money(estimated);
  $("legendRemaining").textContent = money(Math.max(0, remaining));

  const spentPercent = budget > 0
    ? Math.min(actual / budget * 100, 100)
    : 0;

  const estimatePercent = budget > 0
    ? Math.min(estimated / budget * 100, 100)
    : 0;

  $("budgetDonut").style.background =
    `conic-gradient(
      var(--green) 0% ${spentPercent}%,
      var(--orange) ${spentPercent}% ${Math.max(spentPercent, estimatePercent)}%,
      #E8EEE8 ${Math.max(spentPercent, estimatePercent)}% 100%
    )`;

  const filtered = items.filter(item =>
    `${item.name} ${item.category}`
      .toLowerCase()
      .includes(searchQuery)
  );

  const groups = {};

  filtered.forEach(item => {
    if (!groups[item.category]) groups[item.category] = [];
    groups[item.category].push(item);
  });

  $("shoppingItems").innerHTML = Object.keys(groups).length
    ? Object.entries(groups).map(([category, group]) => `
      <div class="category-heading">
        <span>${CATEGORY_ICONS[category] || "🛍️"} ${escapeHTML(category)}</span>
        <span>${group.length} items</span>
      </div>

      ${group.map(item => `
        <div class="grocery-row">
          <input
            type="checkbox"
            aria-label="Mark ${escapeHTML(item.name)} purchased"
            data-check="${item.id}"
            ${item.purchased ? "checked" : ""}
          >

          <span class="food-icon">${getEmoji(item)}</span>

          <div>
            <div class="item-name ${item.purchased ? "done" : ""}">
              ${escapeHTML(item.name)}
            </div>

            <span class="item-details">
              ${item.qty} ${escapeHTML(item.unit)}
              · ${money(item.price)} per ${escapeHTML(item.unit)}
            </span>

            <span class="item-status ${
              item.purchased ? "status-done" : "status-pending"
            }">
              ${item.purchased ? "Purchased" : "To Buy"}
            </span>
          </div>

          <div>
            <div class="item-price">
              ${money(item.qty * (Number(item.price) || 0))}
            </div>
            <button class="delete-btn"
              data-delete="${item.id}"
              aria-label="Delete ${escapeHTML(item.name)}">×</button>
          </div>
        </div>
      `).join("")}
    `).join("")
    : `<div class="empty-state">
        <h3>${searchQuery ? "No matching items" : "Your list is empty"}</h3>
        <p>Add grocery items using the form.</p>
       </div>`;

  $("shoppingItems").querySelectorAll("[data-check]").forEach(input => {
    input.addEventListener("change", () => {
      togglePurchased(Number(input.dataset.check), input.checked);
    });
  });

  $("shoppingItems").querySelectorAll("[data-delete]").forEach(button => {
    button.addEventListener("click", () => {
      deleteItem(Number(button.dataset.delete));
    });
  });

  renderCategories();
  renderBudgetPage();
  renderRecurring();
  renderHistory();
  saveData();
}

/* ADD ITEM */

$("itemForm").addEventListener("submit", event => {
  event.preventDefault();

  const name = $("itemName").value.trim();
  const qty = Number($("itemQty").value);
  const priceText = $("itemPrice").value.trim();
  const price = priceText === "" ? 0 : Number(priceText);

  if (!name || !Number.isFinite(qty) || qty <= 0 ||
      !Number.isFinite(price) || price < 0) {
    toast("Please enter valid item details.");
    return;
  }

  activeList().items.push({
    id: Date.now() + Math.random(),
    name,
    qty,
    unit: $("itemUnit").value,
    category: $("itemCategory").value,
    price,
    actualPrice: null,
    purchased: false
  });

  $("itemName").value = "";
  $("itemQty").value = 1;
  $("itemPrice").value = "";

  $("formMessage").textContent = `${name} added successfully.`;

  renderDashboard();
  toast(`${name} added to your list`);
});

/* PURCHASE CHECKBOX */

function togglePurchased(id, checked) {
  const item = activeList().items.find(item => item.id === id);
  if (!item) return;

  item.purchased = checked;

  if (checked) {
    const actual = prompt(
      `Enter actual price per ${item.unit} for ${item.name}:`,
      item.price
    );

    if (actual !== null && actual.trim() !== "") {
      const price = Number(actual);

      if (Number.isFinite(price) && price >= 0) {
        item.actualPrice = price;
      } else {
        item.actualPrice = item.price;
        toast("Invalid price; estimated price was used.");
      }
    } else {
      item.actualPrice = item.price;
    }
  } else {
    item.actualPrice = null;
  }

  renderDashboard();
  toast(checked ? "Item marked as purchased" : "Item marked as pending");
}

/* DELETE ITEM */

function deleteItem(id) {
  const item = activeList().items.find(item => item.id === id);
  if (!item) return;

  if (!confirm(`Remove "${item.name}" from your shopping list?`)) return;

  activeList().items = activeList().items.filter(item => item.id !== id);
  renderDashboard();
  toast("Item removed");
}

/* SEARCH */

$("searchInput").addEventListener("input", event => {
  searchQuery = event.target.value.trim().toLowerCase();

  if (currentPage !== "dashboard" && currentPage !== "lists") {
    showPage("dashboard");
  }

  renderDashboard();
});

/* SWITCH LIST */

$("listSelect").addEventListener("change", event => {
  currentList = event.target.value;
  renderDashboard();
});

function refreshListSelect() {
  $("listSelect").innerHTML = Object.entries(lists).map(([key, value]) => `
    <option value="${escapeHTML(key)}">
      ${escapeHTML(value.name)}
    </option>
  `).join("");

  $("listSelect").value = currentList;
}

/* CLEAR PURCHASED ITEMS */

$("clearPurchased").addEventListener("click", () => {
  const count = activeList().items.filter(item => item.purchased).length;

  if (!count) {
    toast("No purchased items to clear.");
    return;
  }

  if (!confirm(`Remove ${count} purchased items?`)) return;

  activeList().items = activeList().items.filter(item => !item.purchased);
  renderDashboard();
  toast("Purchased items cleared");
});

/* FINISH SHOPPING AND SAVE HISTORY */

$("finishShopping").addEventListener("click", () => {
  const items = activeList().items;

  if (!items.length) {
    toast("Your shopping list is empty.");
    return;
  }

  if (items.some(item => !item.purchased)) {
    toast("Please mark all items as purchased first.");
    return;
  }

  history.unshift({
    id: Date.now(),
    name: activeList().name,
    date: new Date().toISOString(),
    total: actualTotal(),
    count: items.length,
    items: clone(items)
  });

  activeList().items = items.map(item => ({
    ...item,
    id: Date.now() + Math.random(),
    purchased: false,
    actualPrice: null
  }));

  renderDashboard();
  toast("Shopping trip saved to history!");
  showPage("history");
});

/* BUDGET MANAGEMENT */

function updateBudget() {
  const value = Number($("budgetInput").value);

  if (!Number.isFinite(value) || value < 0) {
    toast("Enter a valid budget.");
    return;
  }

  activeList().budget = value;
  renderDashboard();
  toast("Budget updated successfully.");
}

$("saveBudget").addEventListener("click", updateBudget);
$("budgetPageButton").addEventListener("click", () => {
  const value = prompt("Enter your new budget in INR:", activeList().budget);

  if (value === null) return;

  const amount = Number(value);

  if (!Number.isFinite(amount) || amount < 0) {
    toast("Enter a valid budget.");
    return;
  }

  activeList().budget = amount;
  renderDashboard();
  toast("Budget updated.");
});

/* CREATE SHOPPING LIST */

$("newListForm").addEventListener("submit", event => {
  event.preventDefault();

  const name = $("newListName").value.trim();

  if (!name) return;

  const key = "list-" + Date.now();

  lists[key] = {
    name,
    budget: 2000,
    items: []
  };

  currentList = key;
  $("newListName").value = "";

  refreshListSelect();
  renderDashboard();
  showPage("dashboard");
  toast("New shopping list created");
});

document.querySelectorAll("[data-open-list]").forEach(button => {
  button.addEventListener("click", () => {
    currentList = button.dataset.openList;
    refreshListSelect();
    renderDashboard();
    showPage("dashboard");
  });
});

/* CATEGORIES */

function renderCategories() {
  $("categoryGrid").innerHTML = CATEGORIES.map(category => {
    const items = activeList().items.filter(
      item => item.category === category
    );

    return `
      <div class="category-tile">
        <div style="font-size:27px">
          ${CATEGORY_ICONS[category]}
        </div>
        <h3>${escapeHTML(category)}</h3>
        <p>${items.length} items in current list</p>
        <p style="margin-top:8px;font-weight:bold;color:var(--green)">
          ${money(estimatedTotal(items))}
        </p>
      </div>
    `;
  }).join("");
}

/* BUDGET PAGE */

function renderBudgetPage() {
  const budget = activeList().budget;
  const estimated = estimatedTotal();
  const actual = actualTotal();

  $("budgetDetails").innerHTML = `
    <div class="category-tile">
      <h3>💰 Total Budget</h3>
      <p style="font-size:23px;font-weight:bold;color:var(--green)">
        ${money(budget)}
      </p>
    </div>

    <div class="category-tile">
      <h3>🧾 Estimated Cost</h3>
      <p style="font-size:23px;font-weight:bold">
        ${money(estimated)}
      </p>
    </div>

    <div class="category-tile">
      <h3>🛒 Actual Spent</h3>
      <p style="font-size:23px;font-weight:bold">
        ${money(actual)}
      </p>
    </div>

    <div class="category-tile">
      <h3>▱ Budget Remaining</h3>
      <p style="font-size:23px;font-weight:bold;color:var(--green)">
        ${money(budget - actual)}
      </p>
    </div>
  `;
}

/* RECURRING LIST TEMPLATES */

function saveRecurringList() {
  const existing = recurring.findIndex(
    item => item.key === currentList
  );

  const template = {
    key: currentList,
    name: activeList().name,
    budget: activeList().budget,
    items: clone(activeList().items)
  };

  if (existing >= 0) {
    recurring[existing] = template;
  } else {
    recurring.push(template);
  }

  renderRecurring();
  saveData();
  toast("Recurring list template saved");
}

function renderRecurring() {
  $("recurringItems").innerHTML = recurring.length
    ? recurring.map((template, index) => `
      <div class="saved-row">
        <div>
          <strong>${escapeHTML(template.name)}</strong>
          <small>
            ${template.items.length} items ·
            Budget ${money(template.budget)}
          </small>
        </div>
        <button class="btn btn-outline"
          data-load-template="${index}">
          Use Template
        </button>
      </div>
    `).join("")
    : `<div class="empty-state">
        <h3>No saved templates yet</h3>
        <p>Save a shopping list to reuse it later.</p>
       </div>`;

  $("recurringItems").querySelectorAll("[data-load-template]")
    .forEach(button => {
      button.addEventListener("click", () => {
        loadTemplate(Number(button.dataset.loadTemplate));
      });
    });
}

function loadTemplate(index) {
  const template = recurring[index];
  if (!template) return;

  const key = "list-" + Date.now();

  lists[key] = {
    name: template.name + " Copy",
    budget: template.budget,
    items: template.items.map(item => ({
      ...item,
      id: Date.now() + Math.random(),
      purchased: false,
      actualPrice: null
    }))
  };

  currentList = key;
  refreshListSelect();
  renderDashboard();
  showPage("dashboard");
  toast("Shopping list created from template");
}

$("saveRecurring").addEventListener("click", saveRecurringList);

/* SHOPPING HISTORY */

function renderHistory() {
  $("historyItems").innerHTML = history.length
    ? history.map(trip => `
      <div class="history-row">
        <div>
          <strong>${escapeHTML(trip.name)}</strong>
          <small>
            ${new Date(trip.date).toLocaleString("en-IN")}
            · ${trip.count} items
          </small>
        </div>
        <strong>${money(trip.total)}</strong>
      </div>
    `).join("")
    : `<div class="empty-state">
        <h3>No shopping trips yet</h3>
        <p>Completed shopping trips will appear here.</p>
       </div>`;
}

/* PAGE NAVIGATION */

function showPage(page) {
  currentPage = page;

  document.querySelectorAll(".page-view").forEach(section => {
    section.classList.toggle("active", section.id === page);
  });

  document.querySelectorAll("[data-page]").forEach(button => {
    button.classList.toggle("active", button.dataset.page === page);
  });

  const titles = {
    dashboard: "Hello, Shopper! 👋",
    lists: "My Shopping Lists",
    categories: "Grocery Categories",
    budget: "Budget & Expenses",
    recurring: "Saved & Recurring Lists",
    history: "Shopping History",
    settings: "Settings"
  };

  const subtitles = {
    dashboard: "Let's make your grocery shopping simple and smart.",
    lists: "Manage all your grocery lists in one place.",
    categories: "Organize your groceries by category.",
    budget: "Keep your grocery spending under control.",
    recurring: "Reuse your favorite shopping lists.",
    history: "Review your completed shopping trips.",
    settings: "Manage your FreshList preferences."
  };

  $("welcomeTitle").textContent = titles[page] || "FreshList";
  $("welcomeSubtitle").textContent = subtitles[page] || "";

  window.scrollTo({top: 0, behavior: "smooth"});
}

document.querySelectorAll("[data-page]").forEach(button => {
  button.addEventListener("click", () => {
    showPage(button.dataset.page);
  });
});

/* RESET DEMO DATA */

$("resetData").addEventListener("click", () => {
  if (!confirm("Delete all saved FreshList data and restore the demo?")) {
    return;
  }

  localStorage.removeItem("freshlist-lists");
  localStorage.removeItem("freshlist-history");
  localStorage.removeItem("freshlist-recurring");

  lists = clone(DEFAULT_LISTS);
  history = [];
  recurring = [];
  currentList = "weekly";
  searchQuery = "";

  $("searchInput").value = "";

  refreshListSelect();
  renderDashboard();
  showPage("dashboard");

  toast("Demo data has been reset");
});

/* INITIALIZE */

$("todayDate").textContent = new Date().toLocaleDateString("en-IN", {
  weekday: "short",
  day: "numeric",
  month: "short",
  year: "numeric"
});

$("year").textContent = new Date().getFullYear();

refreshListSelect();
renderDashboard();
showPage("dashboard");

</script>

</body>
</html>
