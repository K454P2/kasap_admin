// KASAP ADMIN - HANYA untuk admin. JANGAN upload ke repo publik / jangan share link-nya.
var SUPA_URL = 'https://zgliygdpbaorutzttxlr.supabase.co';
var SUPA_KEY = 'sb_publishable_o7z4YitotXfBKTSR67YScg_pcBRFS84';
async function load(){
  const res = await fetch(SUPA_URL + '/rest/v1/products?select=*&order=id.asc', {headers:{'apikey':SUPA_KEY,'Authorization':'Bearer '+SUPA_KEY}});
  const data = await res.json();
  document.getElementById('stats').textContent = 'Total produk: ' + data.length + ' | Total stok: ' + data.reduce((s,p)=>s+(p.stok||0),0);
  document.getElementById('productGrid').innerHTML = data.map(p=>`<div class="product"><b>${p.nama}</b><br>Rp ${p.harga.toLocaleString('id-ID')} - Stok ${p.stok}</div>`).join('');
}
load();
