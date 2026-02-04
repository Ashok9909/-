<!DOCTYPE html><html lang="gu">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gujarati Farsan Bill</title>
  <style>
    body { font-family: 'Noto Sans Gujarati', Arial, sans-serif; background:#e9e9e9; padding:10px; }
    .bill { max-width:420px; margin:auto; background:#f9e66b; padding:12px; border:1px solid #333; }
    .header { text-align:center; font-weight:bold; }
    .header h2 { margin:4px 0; }
    .top-info, .meta { font-size:13px; display:flex; justify-content:space-between; margin:4px 0; }
    table { width:100%; border-collapse:collapse; margin-top:8px; font-size:13px; }
    th, td { border:1px solid #333; padding:4px; text-align:center; }
    th { background:#f1d84c; }
    .right { text-align:right; }
    .total-box { margin-top:8px; font-weight:bold; font-size:15px; text-align:right; }
    .footer { margin-top:10px; font-size:13px; display:flex; justify-content:space-between; }
    .controls { max-width:420px; margin:10px auto; background:#fff; padding:10px; border-radius:6px; }
    input, select { width:100%; padding:6px; margin:4px 0; }
    button { width:100%; padding:8px; background:#2d7f3f; color:#fff; border:none; border-radius:4px; }
  </style>
</head>
<body><div class="controls">
  <input type="text" id="customer" placeholder="ગ્રાહકનું નામ" />
  <select id="itemSelect"></select>
  <input type="number" id="qty" placeholder="વજન / Qty" value="1" />
  <button onclick="addItem()">વસ્તુ ઉમેરો</button>
</div><div class="bill">
  <div class="header">
    <h2>શ્રી ગણેશાય નમઃ</h2>
    <div>મારુતિ માર્કેટિંગ</div>
  </div>  <div class="top-info">
    <div>ગ્રાહક: <span id="custName">---</span></div>
    <div>તારીખ: <span id="date"></span></div>
  </div>  <table>
    <thead>
      <tr>
        <th>નં</th>
        <th>વસ્તુ</th>
        <th>ભાવ</th>
        <th>Qty</th>
        <th>ટોટલ</th>
      </tr>
    </thead>
    <tbody id="billBody"></tbody>
  </table>  <div class="total-box">કુલ રકમ: ₹ <span id="grandTotal">0</span></div>  <div class="footer">
    <div>કુલ આઇટમ: <span id="count">0</span></div>
    <div>આભાર </div>
  </div>
</div><script>
const items = [
  {name:'સેવ', price:120},{name:'ગાંઠિયા', price:120},{name:'જી.સેવ', price:120},{name:'ભાઠા', price:120},
  {name:'મારવાડી', price:120},{name:'તીખુ', price:120},{name:'મકાઇ', price:120},{name:'નડિયાદી', price:120},
  {name:'પંજાબી', price:120},{name:'લસણ', price:120},{name:'ચોખા પવા', price:120},{name:'વટાણા', price:100},
  {name:'દાળ', price:130},{name:'શિંગભજીયા', price:130},{name:'મસાલા સિંગ', price:130},
  {name:'T બુન્દી', price:140},{name:'M બુન્દી', price:140},{name:'T ફરાળી', price:135},{name:'M ફરાળી', price:135},
  {name:'કેળા', price:160},{name:'બટેકા વેફર', price:175},{name:'200g વેફર', price:180},
  {name:'T ફરાળીR', price:175},{name:'M ફરાળીR', price:175},{name:'200g Mફરાળી', price:215},
  {name:'200g Tફરાળી', price:215},{name:'Rવેફર', price:200},{name:'200g વેફર R', price:210},
  {name:'T. 10₹Patti R', price:105},{name:'M. 10₹ Patti', price:105},
  {name:'ભાખરવડી M', price:105},{name:'ભાખરવડી N', price:105},
  {name:'મોળી કળી', price:130},{name:'સકરપારા', price:105}
];

const sel = document.getElementById('itemSelect');
items.forEach((it,i)=>{ let o=document.createElement('option'); o.value=i; o.text=it.name+' ₹'+it.price; sel.add(o); });

let total=0, count=0;
document.getElementById('date').innerText = new Date().toLocaleDateString();

function addItem(){
  const idx=sel.value; const qty=parseFloat(document.getElementById('qty').value);
  const it=items[idx]; const rowTotal=it.price*qty;
  count++; total+=rowTotal;
  document.getElementById('custName').innerText = document.getElementById('customer').value || '---';
  const tr=document.createElement('tr');
  tr.innerHTML=`<td>${count}</td><td>${it.name}</td><td>${it.price}</td><td>${qty}</td><td>${rowTotal.toFixed(2)}</td>`;
  document.getElementById('billBody').appendChild(tr);
  document.getElementById('grandTotal').innerText=total.toFixed(2);
  document.getElementById('count').innerText=count;
}
</script></body>
</html>
