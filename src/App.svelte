<script>
    let invoice = "INV-DE0001-202111-001";
    let name1 = "John Doe";
    let name2 = "John Goe";

    let address1 = "Address 1";
    let address2 = "Address 2";

    let email1 = "email1@gmail.com";
    let email2 = "email2@gmail.com";

    let phone1 = "9876543210";
    let phone2 = "9876543210";
    

    let defaultItem = {
        name: "Item 1",
        qty: 1,
        price: 500
    }

    let items = [
        {...defaultItem}
    ]

    let handleAddItem = () => {
        let newItem = {...defaultItem};
        newItem.name = `Item ${items.length + 1}`
        items = [...items, newItem]
    }
</script>

<main>
    <h1 class="print-only">Invoice: {invoice} </h1>
    <input type="text" bind:value={invoice}/>

    <section class="info-list">

        <div class="names info-item">
            <div class="name from">
                <h4>From</h4>
                <div class="print-only">{name1}</div>
                <textarea bind:value={name1}/>
            </div>
            <div class="name to">
                <h4>To</h4>
                <div class="print-only">{name2}</div>
                <textarea bind:value={name2}/>
            </div>
        </div>

        <div class="addresses info-item">
            <div class="address from">
                <h4>Address</h4>
                <div class="print-only">{address1}</div>
                <textarea bind:value={address1}/>
            </div>
            <div class="address to">
                <h4>Address</h4>
                <div class="print-only">{address2}</div>
                <textarea bind:value={address2}/>
            </div>
        </div>

        <div class="emails info-item">
            <div class="email from">
                <h4>Email</h4>
                <div class="print-only">{email1}</div>
                <textarea bind:value={email1}/>
            </div>
            <div class="email to">
                <h4>Email</h4>
                <div class="print-only">{email2}</div>
                <textarea bind:value={email2}/>
            </div>
        </div>

        <div class="phone-numbers info-item">
            <div class="phone from">
                <h4>Phone #</h4>
                <div class="print-only">{phone1}</div>
                <textarea bind:value={phone1}/>
            </div>
            <div class="phone to">
                <h4>Phone #</h4>
                <div class="print-only">{phone2}</div>
                <textarea bind:value={phone2}/>
            </div>
        </div>

    </section>

    <section class="items">
        <table width="100%" border="1">
            <thead>
                <tr>
                    <th width="40">#</th>
                    <th align="left">Item</th>
                    <th align="right" width="100">Quantity</th>
                    <th align="right" width="100">Price</th>
                    <th align="right" width="100">Amount</th>
                </tr>
            </thead>
            <tbody contenteditable="true">
                {#each items as item, i}
                    <tr>
                        <td>{i+1}</td>
                        <td align="left">{item.name}</td>
                        <td align="right">{item.qty}</td>
                        <td align="right">{item.price}</td>
                        <td align="right">{item.qty * item.price}</td>
                    </tr>
                {/each}
            </tbody>
        </table>
        <button on:click={handleAddItem}>+ Add Item</button>
    </section>
</main>

<style>
    h1, h2, h3, h4, h5, h6 { margin: 0; }
    input, textarea { width: 100%; }

	main {
		text-align: center;
		padding: 1em;
		max-width: 768px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

    .info-list .info-item {
        display: flex;
        flex: 1;
    }

    .info-list .info-item > div {
        width: 100%;
        flex: 1;
        text-align: left;
    }

    @media not print {
        .print-only { display: none; }
    }
</style>