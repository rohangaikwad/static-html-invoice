<script>
    let invoice = "Invoice: INV-DE0001-202111-001";
    let name1 = "Rohan Gaikwad";
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

    let handleRemoveItem = () => {
        console.log(23)
    }

    let dt = new Date();
    let invoiceDate = `Invoice Date: ${dt.toLocaleDateString("en-US", {month: 'long', day: 'numeric', year: "numeric"})}`
</script>

<main>
    <div class="invoice-details">
        <input type="text" bind:value={invoice} class="invoice-number"/>
        <div><input type="text" bind:value={invoiceDate} class="invoice-date"/></div>
    </div>

    <section class="info-list">

        <div class="names info-item">
            <div class="name from">
                <h4>From</h4>
                <div contenteditable="true" spellcheck="false" class="fake-input">{name1}</div>
            </div>
            <div class="name to">
                <h4>Bill To</h4>
                <div contenteditable="true" spellcheck="false" class="fake-input">{name2}</div>
            </div>
        </div>

        <div class="addresses info-item">
            <div class="address from">
                <h4>Address</h4>
                <div contenteditable="true" spellcheck="false" class="fake-input">{address1}</div>
            </div>
            <div class="address to">
                <h4>Address</h4>
                <div contenteditable="true" spellcheck="false" class="fake-input">{address2}</div>
            </div>
        </div>

        <div class="emails info-item">
            <div class="email from">
                <h4>Email</h4>
                <div class="print-only">{email1}</div>
                <input type="text" bind:value={email1}/>
            </div>
            <div class="email to">
                <h4>Email</h4>
                <div class="print-only">{email2}</div>
                <input type="text" bind:value={email2}/>
            </div>
        </div>

        <div class="phone-numbers info-item">
            <div class="phone from">
                <h4>Phone #</h4>
                <div class="print-only">{phone1}</div>
                <input type="text" bind:value={phone1}/>
            </div>
            <div class="phone to">
                <h4>Phone #</h4>
                <div class="print-only">{phone2}</div>
                <input type="text" bind:value={phone2}/>
            </div>
        </div>

    </section>

    <section class="items">
        <table width="100%" cellspacing="2">
            <thead>
                <tr>
                    <th width="30">#</th>
                    <th align="left">Item</th>
                    <th align="right" width="95">Quantity</th>
                    <th align="right" width="95">Price</th>
                    <th align="right" width="95">Amount</th>
                </tr>
            </thead>
            <tbody>
                {#each items as item, i}
                    <tr>
                        <td align="center">{i+1}</td>
                        <td contenteditable="true" align="left">{item.name}</td>
                        <td contenteditable="true" align="right">{item.qty}</td>
                        <td contenteditable="true" align="right">₹{item.price}</td>
                        <td contenteditable="true" align="right">₹{item.qty * item.price}</td>
                    </tr>
                {/each}
                <tr>
                    <td colspan="4" align="right">Taxes & Charges</td>
                    <td align="right" width="95">₹500</td>
                </tr>
            </tbody>
        </table>
        <div class="actions print-hide">
            <button on:click={handleAddItem}>+ Add Item</button>
            <button on:click={handleRemoveItem}>+ Remove Item</button>
        </div>
        <div class="total">
            <div class="text">Total:</div>
            <div class="val" contenteditable="true">₹500</div>
        </div>
    </section>

    <section class="thanks">
        Thank you for your business!
    </section>
</main>

<style>
    * { box-sizing: border-box; }
    body { margin: 0; }

    h1, h2, h3, h4, h5, h6 { margin: 0; }
    input, textarea { width: 100%; border: none!important; resize: none; outline: none!important; background: transparent; }

	main {
		height: calc(297px * 3.75);
        max-width: calc(210px * 3.75);
		margin: 0 auto;
        background: #fff;
        padding: 0 80px;
	}

    .invoice-details { padding: 60px 0 40px;}
    .invoice-details * { text-align: right; }
    .invoice-number { font-size: 30px; font-weight: 700; padding: 0; margin-bottom: 0; }

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

    .info-list .info-item h4 {
        font-size: 14px; color: #a8adbc;
        font-weight: 400;
    }

    .info-list .info-item input,
    .info-list .info-item textarea{
        padding: 0px 0px; color: #465373; 
        font-weight: 500; font-size: 16px;
    }

    .fake-input {
        margin-bottom: 9px; color: #465373; 
        font-weight: 500; font-size: 16px;
    }

    table { background: #fcfdff; border: solid 1px #ecedf5; border-radius: 5px; table-layout: fixed; margin-top: 30px; }
    th, td { background: #ffffff; border: solid 1px #ecedf5; }
    th { padding: 10px 15px; font-size: 14px; }
    td { padding: 10px 15px;}

    .total {
        background-color: #f8f9fc;
        border: solid 1px #ecedf5;
        border-radius: 0 0 5px 5px;
        display: flex; padding: 10px 15px;
        justify-content: flex-end;
        font-size: 20px; font-weight: 700;
        margin-bottom: 80px;
    }

    .total .text { margin-right: 100px; }

    .thanks { font-weight: 500; }

    @media not print {
        .print-only { display: none; }
    }
</style>