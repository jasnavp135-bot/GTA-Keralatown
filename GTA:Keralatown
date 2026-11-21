<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>City Life 3D</title>
<style>
:root{--ui:rgba(255,255,255,.85);--uitext:#1d2733;--uib:rgba(0,0,0,.15);box-sizing:border-box}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--ui:rgba(18,24,34,.8);--uitext:#e6edf5;--uib:rgba(255,255,255,.2)}}
:root[data-theme="dark"]{--ui:rgba(18,24,34,.8);--uitext:#e6edf5;--uib:rgba(255,255,255,.2)}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent;user-select:none;-webkit-user-select:none}
html,body{height:100%;margin:0}
body{background:#8fcdf0;font-family:"Trebuchet MS","Segoe UI",system-ui,sans-serif;overflow:hidden;touch-action:none}
canvas{position:fixed;inset:0;width:100%;height:100%;display:block}
.hud{position:fixed;top:0;left:0;right:64px;padding:calc(env(safe-area-inset-top,0px) + 10px) 12px 0;display:flex;flex-wrap:wrap;gap:6px;pointer-events:none}
.chip{background:var(--ui);color:var(--uitext);border:1px solid var(--uib);border-radius:12px;padding:6px 12px;font-size:.95rem}
#hint{position:fixed;left:50%;transform:translateX(-50%);bottom:calc(env(safe-area-inset-bottom,0px) + 150px);display:none;pointer-events:none}
#start{position:fixed;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;text-align:center;padding:24px;background:rgba(12,20,32,.62);color:#fff;cursor:pointer}
#start h1{margin:0;font-size:2rem}#start p{margin:0;max-width:430px;line-height:1.5}
.tb{position:fixed;display:none;border:2px solid rgba(255,255,255,.7);background:rgba(0,0,0,.3);color:#fff;border-radius:50%;font-size:.85rem;align-items:center;justify-content:center;touch-action:none}
#bj{right:calc(env(safe-area-inset-right,0px) + 20px);bottom:calc(env(safe-area-inset-bottom,0px) + 26px);width:72px;height:72px}
#bs{right:100px;bottom:calc(env(safe-area-inset-bottom,0px) + 22px);width:56px;height:56px}
#bf{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 110px);width:78px;height:78px;background:rgba(217,72,91,.55)}
#bd{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 90px);width:56px;height:56px;background:rgba(40,120,200,.55)}
#bu{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 152px);width:56px;height:56px;background:rgba(60,160,90,.55)}
#bw{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 198px);width:56px;height:56px}
#joy{position:fixed;display:none;width:110px;height:110px;margin:-55px 0 0 -55px;border-radius:50%;border:2px solid rgba(255,255,255,.6);background:rgba(255,255,255,.12);pointer-events:none}
#joy i{position:absolute;left:35px;top:35px;width:40px;height:40px;border-radius:50%;background:rgba(255,255,255,.75)}
.touch .tb{display:flex}.touch .desk{display:none}.touch #hint{bottom:calc(env(safe-area-inset-bottom,0px) + 200px)}

.hp{width:110px;height:14px;padding:0;overflow:hidden;align-self:center}#hpf{height:100%;width:100%;background:#d9485b;transition:width .2s}
#toast{position:fixed;top:calc(env(safe-area-inset-top,0px) + 66px);left:50%;transform:translateX(-50%);max-width:88vw;text-align:center;background:var(--ui);color:var(--uitext);border:1px solid var(--uib);border-radius:12px;padding:8px 14px;opacity:0;transition:opacity .3s;pointer-events:none}
#bust{position:fixed;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,.72);color:#fff;font-size:2.1rem;font-weight:bold;text-align:center;padding:20px;opacity:0;pointer-events:none;transition:opacity .5s}
#cross2{position:fixed;left:50%;top:50%;width:8px;height:8px;margin:-4px 0 0 -4px;border-radius:50%;background:#fff;box-shadow:0 0 3px #000;display:none;pointer-events:none}
#bph{position:fixed;right:calc(env(safe-area-inset-right,0px) + 12px);top:calc(env(safe-area-inset-top,0px) + 8px);width:48px;height:48px;border-radius:14px;border:1px solid var(--uib);background:var(--ui);font-size:1.4rem}
#phone{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.45);padding:calc(env(safe-area-inset-top,0px) + 10px) 10px calc(env(safe-area-inset-bottom,0px) + 10px)}
#pframe{width:min(330px,94vw);max-height:100%;display:flex;flex-direction:column;background:#10151d;border:4px solid #2b3442;border-radius:28px;padding:14px;color:#e6edf5;overflow:auto}
#pscr{min-height:360px}#pscr h3{margin:4px 0 12px;text-align:center}
.apps{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}.apps button{display:flex;flex-direction:column;align-items:center;gap:4px;padding:12px 4px;border:0;border-radius:16px;background:#243044;color:#e6edf5;font-size:.8rem}.apps b{font-size:1.7rem}
.disp{font-size:2rem;letter-spacing:.3em;text-align:center;background:#0a0e14;border-radius:12px;padding:10px;margin-bottom:10px;min-height:56px}
.pad{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}.pad button,.big{padding:14px 0;border:0;border-radius:12px;background:#243044;color:#e6edf5;font-size:1.2rem}.big{width:100%;margin-top:10px;background:#2f78b5}
.msg{text-align:center;min-height:1.4em;color:#ffd98a}
#pnav{display:flex;gap:10px;margin-top:10px}#pnav button{flex:1;padding:10px;border:0;border-radius:12px;background:#243044;color:#e6edf5}
.sw{display:inline-block;width:44px;height:44px;border-radius:50%;border:2px solid #fff;margin:6px}

#extras{position:fixed;right:calc(env(safe-area-inset-right,0px) + 12px);top:calc(env(safe-area-inset-top,0px) + 64px);display:flex;flex-direction:column;gap:7px}
#extras button{border:1px solid var(--uib);border-radius:12px;background:var(--ui);color:var(--uitext);padding:9px 11px;font-weight:700}
#jobhud{position:fixed;left:50%;top:calc(env(safe-area-inset-top,0px) + 62px);transform:translateX(-50%);display:none;max-width:88vw;text-align:center}
#weather{font-size:.8rem}
.jb{display:none!important}.touch.jcbmode .jb{display:flex!important}.touch.jcbmode #bf,.touch.jcbmode #bu,.touch.jcbmode #bw{display:none!important}
#jd{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 110px);width:78px;height:78px;background:rgba(60,160,90,.6)}
#ju{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 198px);width:56px;height:56px}
#jl{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 152px);width:56px;height:56px}
#jk{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 262px);width:56px;height:56px}
.vlist{max-height:330px;overflow:auto;display:flex;flex-direction:column;gap:6px}.vrow{display:flex;justify-content:space-between;padding:10px 12px;border:0;border-radius:10px;background:#243044;color:#e6edf5;font-size:.95rem}
.ab{display:none!important}.touch.airmode .ab{display:flex!important}.touch.airmode #bf,.touch.airmode #bu,.touch.airmode #bw{display:none!important}
#au{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 198px);width:56px;height:56px}
#ad{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 152px);width:56px;height:56px}
#bx{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 262px);width:56px;height:56px}
.cb{display:none!important}.touch.carmode .cb{display:flex!important}.touch.carmode #bf,.touch.carmode #bw{display:none!important}.touch.carmode #bu{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 262px)}
#cg{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 110px);width:78px;height:78px;background:rgba(60,160,90,.6)}
#ck{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 152px);width:56px;height:56px;background:rgba(217,72,91,.55)}
#ce{right:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 198px);width:56px;height:56px}
#cn{right:108px;bottom:calc(env(safe-area-inset-bottom,0px) + 214px);width:56px;height:56px}
#cl{left:16px;bottom:calc(env(safe-area-inset-bottom,0px) + 40px);width:66px;height:66px}
#cr{left:94px;bottom:calc(env(safe-area-inset-bottom,0px) + 40px);width:66px;height:66px}
</style>
</head>
<body>
<div class="hud"><div class="chip" id="clk">12:00</div><div class="chip" id="spd" style="display:none">0 km/h</div><div class="chip" id="mon">$500</div><div class="chip hp"><div id="hpf"></div></div><div class="chip" id="wan"></div><div class="chip" id="wpn"></div></div>
<div class="chip" id="hint">Press E to drive</div>
<div id="start"><h1>City Streets 3D</h1><p>You wake up at home. Explore a bigger-feeling city, buy 8 vehicles, use 7 weapons, earn money with taxi and delivery jobs, change weather, eat, drive and open your phone (P) to order vehicles, see the map and ride the bus.</p>
<p class="desk">WASD move, mouse look, click fire, 1-7 weapons, F use or buy, E vehicle, P phone, G weather, J delivery job, Shift run, Space jump. Vehicles: W/S gas and brake, A/D steer. Aircraft: Space or R up, Shift or V down, X flying car. Bus: stand near a stopped bus and press E. Weapons: 0-9 select, B detonate bombs. Car: I engine, L lights, E steal a car.</p>
<p><b>Tap or click to start</b></p></div>
<button class="tb" id="bj">Jump</button><button class="tb" id="bs">Run</button><button class="tb" id="bd">Drive</button><button class="tb jb" id="jd">Dig</button><button class="tb jb" id="ju">Arm ▲</button><button class="tb jb" id="jl">Arm ▼</button><button class="tb jb" id="jk">Bucket</button><button class="tb ab" id="au">Up</button><button class="tb ab" id="ad">Down</button><button class="tb ab" id="bx">Fly</button><button class="tb cb" id="cg">Gas</button><button class="tb cb" id="ck">Brake</button><button class="tb cb" id="ce">Engine</button><button class="tb cb" id="cn">Lights</button><button class="tb cb" id="cl">&#9664;</button><button class="tb cb" id="cr">&#9654;</button><button class="tb" id="bf">Fire</button><button class="tb" id="bu">Use</button><button class="tb" id="bw">Gun</button>
<div id="toast"></div><div id="bust"></div><div id="cross2"></div><button id="bph" aria-label="Phone">📱</button><div id="extras"><button id="weatherBtn">🌤️ Weather</button><button id="jobBtn">📦 Job</button></div><div class="chip" id="jobhud"></div><div id="phone"><div id="pframe"><div id="pscr"></div><div id="pnav"><button id="phome">Home</button><button id="pclose">Close</button></div></div></div><div id="joy"><i></i></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
(function(){
var touch=matchMedia('(pointer:coarse)').matches;if(touch)document.body.classList.add('touch');
var W=innerWidth,Ht=innerHeight;
var R=new THREE.WebGLRenderer({antialias:true});R.setPixelRatio(Math.min(devicePixelRatio||1,1.5));R.setSize(W,Ht);document.body.prepend(R.domElement);
var scene=new THREE.Scene();scene.background=new THREE.Color(0x8fcdf0);scene.fog=new THREE.Fog(0x8fcdf0,120,900);
var cam=new THREE.PerspectiveCamera(65,W/Ht,.1,2500);
var hemi=new THREE.HemisphereLight(0xdff0ff,0x555560,.9),sun=new THREE.DirectionalLight(0xfff2d0,.8);sun.position.set(150,200,80);scene.add(hemi,sun);
addEventListener('resize',function(){W=innerWidth;Ht=innerHeight;R.setSize(W,Ht);cam.aspect=W/Ht;cam.updateProjectionMatrix()});
function hash(a,b,s){var h=Math.imul(a|0,374761393)+Math.imul(b|0,668265263)+Math.imul(s,1442695041);h=Math.imul(h^(h>>>13),1274126177);h^=h>>>16;return(h>>>0)/4294967295}
function M(c){return new THREE.MeshLambertMaterial({color:c})}
function box(w,h,d,c,x,y,z){var m=new THREE.Mesh(new THREE.BoxGeometry(w,h,d),M(c));m.position.set(x,y,z);return m}

// layout
var CELL=50,ROAD=14,N=10,HALF=N*CELL/2;
function rc(r){return (r-N/2)*CELL}
function onBlock(x,z){if(Math.abs(x)>=HALF||Math.abs(z)>=HALF)return false;var u=(x+HALF)%CELL,v=(z+HALF)%CELL;return u>7&&u<CELL-7&&v>7&&v<CELL-7}
function ground(x,z){return onBlock(x,z)?.25:0}
var pl=new THREE.Mesh(new THREE.PlaneGeometry(HALF*2+30,HALF*2+30).rotateX(-Math.PI/2),M(0x2f343b));pl.position.y=0;scene.add(pl);
var gr=new THREE.Mesh(new THREE.PlaneGeometry(700,700).rotateX(-Math.PI/2),M(0x56904d));gr.position.y=-.1;scene.add(gr);

// ---- places, shops and zones
var boxes=[],zones=[],SPECIAL={},money=3000,owned=[],polExit={x:10,z:-25},hosExit={x:-9,z:25};
var MODELS={hatch:{n:'City Hatch',price:2000,col:0xd94a4a,sc:[.9,.9,.85],top:30,acc:15,turn:2},sedan:{n:'Sedan',price:4500,col:0x3a6bc8,sc:[1,1,1],top:34,acc:17,turn:1.9},suv:{n:'SUV',price:8000,col:0x3aa05a,sc:[1.12,1.25,1.05],top:32,acc:16,turn:1.7},sports:{n:'Sports Car',price:12000,col:0xf0702a,sc:[1,.82,1.05],top:48,acc:26,turn:2},
 pickup:{n:'Pickup Truck',price:9500,col:0x9b7653,sc:[1.2,1.15,1.25],top:29,acc:14,turn:1.55},
 electric:{n:'Electric GT',price:16000,col:0x22b8a5,sc:[1,.8,1.1],top:52,acc:30,turn:2.2},
 van:{n:'City Van',price:7000,col:0xddd9ce,sc:[1.2,1.25,1.25],top:27,acc:13,turn:1.45},
 super:{n:'Supercar',price:24000,col:0x8b55d8,sc:[1,.78,1.12],top:62,acc:34,turn:2.35}};
function label(txt,w,h,bg){var c=document.createElement('canvas');c.width=256;c.height=64;var x=c.getContext('2d');x.fillStyle=bg||'#1d2733';x.fillRect(0,0,256,64);x.fillStyle='#fff';x.font='bold 28px sans-serif';x.textAlign='center';x.textBaseline='middle';x.fillText(txt,128,34,244);var s=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(c)}));s.scale.set(w,h,1);return s}
function shell(cx,cz,w,d,h,col,ds,dw){var t=.6,mat=M(col),xf=cx+ds*w/2,xb=cx-ds*w/2,zl=cz-d/2,zr=cz+d/2;
 function wall(x0,x1,z0,z1){var m=new THREE.Mesh(new THREE.BoxGeometry(x1-x0,h,z1-z0),mat);m.position.set((x0+x1)/2,h/2+.25,(z0+z1)/2);scene.add(m);boxes.push([x0,x1,z0,z1,h+.25])}
 wall(xb-t/2,xb+t/2,zl-t/2,zr+t/2);wall(cx-w/2-t/2,cx+w/2+t/2,zl-t/2,zl+t/2);wall(cx-w/2-t/2,cx+w/2+t/2,zr-t/2,zr+t/2);
 wall(xf-t/2,xf+t/2,zl-t/2,cz-dw/2);wall(xf-t/2,xf+t/2,cz+dw/2,zr+t/2);
 scene.add(box(w+t,.5,d+t,col,cx,h+.5,cz),box(w,.06,d,0xd5ccb8,cx,.22,cz))}
function sign(txt,w,h,bg,x,y,z){var s=label(txt,w,h,bg);s.position.set(x,y,z);scene.add(s)}
function heal(n){hp=Math.min(100,hp+n)}
function house(cx,cz){shell(cx,cz,16,14,5,0xe8d9b8,-1,3.5);sign('HOME',7,1.8,'#7a4b2a',cx,8,cz);
 scene.add(box(3,.5,2,0x3a6bc8,cx+6,.6,cz-4),box(1,.2,1.6,0xffffff,cx+7.3,.9,cz-4),box(2,.9,1.4,0x6b4423,cx-1,.7,cz+4.5),box(1,2,1,0xdddddd,cx+7,1.25,cz+4.5));
 boxes.push([cx+4.5,cx+7.5,cz-5,cz-3,1],[cx-2,cx,cz+3.8,cz+5.2,1],[cx+6.5,cx+7.5,cz+4,cz+5,2.3]);
 zones.push({x:cx+3.2,z:cz-4,r:2.6,l:function(){return 'Sleep until morning'},f:function(){clock=0;hp=100;toast('You slept well. Health restored.')}},
 {x:cx+5,z:cz+4,r:2.6,l:function(){return 'Eat from the fridge (+10 HP)'},f:function(){heal(10);toast('Snack time! +10 HP')}})}
function hospital(cx,cz){shell(cx,cz,26,24,8,0xf2f4f6,1,6);sign('HOSPITAL',9,2.2,'#c0392b',cx,12,cz);
 scene.add(box(.3,3.6,1.1,0xd32f2f,cx+13.5,6,cz),box(.3,1.1,3.6,0xd32f2f,cx+13.5,6,cz),box(1.2,1.1,7,0x8a9aa8,cx+3,.85,cz));boxes.push([cx+2.4,cx+3.6,cz-3.5,cz+3.5,1.4]);
 for(var i=0;i<3;i++){scene.add(box(2,.6,1,0xdfeaf2,cx-9,.6,cz-8+i*5));boxes.push([cx-10,cx-8,cz-8.5+i*5,cz-7.5+i*5,.9])}
 zones.push({x:cx+6,z:cz,r:3.4,l:function(){return 'Get treated ($100, full health)'},f:function(){if(money>=100){money-=100;hp=100;toast('Treated. Health is full.')}else{heal(30);toast('Not enough money. Basic care: +30 HP')}}})}
function policeStn(cx,cz){shell(cx,cz,24,22,7,0x3b5aa0,-1,5);sign('POLICE',8,2,'#1c3c78',cx,10.5,cz);scene.add(box(6,1,1.4,0x555a66,cx+4,.8,cz));boxes.push([cx+1,cx+7,cz-.7,cz+.7,1.3]);polExit={x:cx-15,z:cz}}
function buyCar(k){var m=MODELS[k];if(owned.indexOf(k)>=0){setVehicle(k,-4,-25,0);toast('Your '+m.n+' is ready');return}
 if(money<m.price){toast('Not enough money. You need $'+(m.price-money)+' more for the '+m.n);return}
 money-=m.price;owned.push(k);setVehicle(k,-4,-25,0);toast('You bought the '+m.n+'!')}
function showroom(cx,cz){shell(cx,cz,28,26,7,0xdfe6ee,1,9);sign('CAR SHOWROOM',10,2.4,'#1d2733',cx,10.5,cz);
 Object.keys(MODELS).forEach(function(k,i){var m=MODELS[k],x=cx-10+(i%3)*9,z=cz-9+Math.floor(i/3)*8;
  var pd=new THREE.Mesh(new THREE.CylinderGeometry(3,3,.25,20),M(0x888e99));pd.position.set(x,.38,z);scene.add(pd);
  var g=car(m.col);g.scale.set(m.sc[0],m.sc[1],m.sc[2]);g.position.set(x,.5,z);g.rotation.y=-Math.PI/2;
  sign(m.n+' (free)',6,1.5,'#1d2733',x,4.6,z);boxes.push([x-2.2,x+2.2,z-1.2,z+1.2,2]);
  zones.push({x:x+3.6,z:z,r:2.6,l:function(){return 'Get the '+m.n+' (free)'},f:function(){buyCar(k)}})})}
function kiosk(x,z,col,n,price,g){scene.add(box(2.4,2.2,2.4,col,x,1.35,z),box(3,.2,3,0xffffff,x,2.6,z));sign(n,4,1,'#1d2733',x,3.7,z);boxes.push([x-1.2,x+1.2,z-1.2,z+1.2,2.5]);
 zones.push({x:x,z:z,r:3,l:function(){return 'Buy '+n+' $'+price+' (+'+g+' HP)'},f:function(){if(money>=price){money-=price;heal(g);toast('Yum! +'+g+' HP')}else toast('Not enough money')}})}
function gate(){var z=-HALF-8;scene.add(box(1.8,11,1.8,0x8a8f99,-9,5.7,z),box(1.8,11,1.8,0x8a8f99,9,5.7,z),box(20,2.4,1.6,0x2f5f9e,0,11,z));sign('WELCOME TO CITY STREETS',16,2,'#2f5f9e',0,11,z+1.2);boxes.push([-9.9,-8.1,z-.9,z+.9,12],[8.1,9.9,z-.9,z+.9,12])}
SPECIAL['5,5']=house;SPECIAL['4,5']=hospital;SPECIAL['5,4']=policeStn;SPECIAL['4,4']=showroom;
kiosk(8.5,-16,0xd9892b,'Burger',15,25);kiosk(-8.5,16,0xc0392b,'Pizza',20,35);kiosk(8.5,16,0x4b9a5a,'Salad',10,15);kiosk(8.5,36,0xe0a030,'Juice',8,12);gate();
// ---- dig site next to the house
function lorryModel(col){var g=new THREE.Group();
 g.add(box(2.3,.5,7,0x3a3f48,0,.75,.4),box(2.2,1.7,1.8,col,0,1.9,-2.5),box(2,.7,.05,0x9ec7e0,0,2.45,-3.42));
 var bed=new THREE.Group();bed.add(box(2.4,.15,4.8,0x555b66,0,0,0),box(.15,1,4.8,0x6b7280,-1.2,.5,0),box(.15,1,4.8,0x6b7280,1.2,.5,0),box(2.4,1,.15,0x6b7280,0,.5,2.4),box(2.4,1,.15,0x6b7280,0,.5,-2.4));bed.position.set(0,1.05,1.7);g.add(bed);
 [-2.6,.6,2.8].forEach(function(z){[-1.2,1.2].forEach(function(x){var w=new THREE.Mesh(new THREE.CylinderGeometry(.55,.55,.4,14),M(0x1a1a1a));w.rotation.z=Math.PI/2;w.position.set(x,.55,z);g.add(w)})});
 g.userData.bed=bed;scene.add(g);return g}
var PX=22,PZ=38,pile=40;
var dirt=new THREE.Mesh(new THREE.CylinderGeometry(5,5,.05,24),M(0x5e3f24));dirt.position.set(PX,.26,PZ);scene.add(dirt);
var mound=new THREE.Mesh(new THREE.SphereGeometry(1,14,8),M(0x7a5230));mound.position.set(PX,.25,PZ);mound.scale.set(3.6,2.2,3.6);scene.add(mound);
sign('DIG SITE',6,1.6,'#a0602a',30,5.5,38);
var SL={x:38,z:38,state:'load',load:0,t:0};SL.g=lorryModel(0xd9892b);SL.g.position.set(SL.x,0,SL.z);SL.g.rotation.y=-Math.PI/2;
SL.soil=new THREE.Mesh(new THREE.BoxGeometry(2,1,4.2),M(0x7a5230));SL.soil.position.set(0,.1,0);SL.soil.scale.y=.01;SL.soil.visible=false;SL.g.userData.bed.add(SL.soil);
SL.box=[SL.x-3.8,SL.x+3.8,SL.z-1.4,SL.z+1.4,3];boxes.push(SL.box);
function lorryBed(){return {x:SL.g.position.x+Math.sin(SL.g.rotation.y)*1.7,z:SL.g.position.z+Math.cos(SL.g.rotation.y)*1.7}}



// ---- town extras: houses, shops, school, factories, bus stations and stands
var STOPS=[{x:-100,z:25,stop:8,n:'Station A',st:1},{x:-100,z:-50},{x:-75,z:-50,stop:4,n:'Bus Stand 1'},{x:75,z:-50,stop:4,n:'Bus Stand 2'},{x:100,z:-50},{x:100,z:-25,stop:8,n:'Station B',st:1},{x:100,z:50},{x:75,z:50,stop:4,n:'Bus Stand 3'},{x:-75,z:50,stop:4,n:'Bus Stand 4'},{x:-100,z:50}];
var waiting=[],kids=[],smoke=[],YARD={x0:0,x1:0,z0:0,z1:0},fcool=0;
var HC=[0xe8d9b8,0xd9c7b0,0xcfd8c0,0xe3c9c9,0xc9d6e3],RC=[0x8a3a2a,0x3a4a6a,0x4a6a3a,0x6a4a2a];
function bedAt(x,z,col){scene.add(box(2.2,.5,1.4,col,x,.6,z),box(.6,.2,1,0xffffff,x-.8,.95,z));boxes.push([x-1.1,x+1.1,z-.7,z+.7,.9])}
function smallHouse(x,z,ds,col,roof){shell(x,z,9,8,4,col,ds,2.6);scene.add(box(10,.3,9,roof,x,5.1,z));bedAt(x-ds*2.8,z-2,0x3a6bc8)}
function houseBlock(cx,cz){for(var a=0;a<2;a++)for(var b=0;b<2;b++){var k=Math.floor(Math.abs(cx*3+cz*7+a*5+b*11)/7)%5;smallHouse(cx+(a?9.5:-9.5),cz+(b?9.5:-9.5),a?1:-1,HC[k],RC[k%4])}}
function shelf(x,z,w,d,col){scene.add(box(w,1.6,d,0x8a8f99,x,1.05,z),box(w-.2,.3,d-.2,col,x,2,z));boxes.push([x-w/2,x+w/2,z-d/2,z+d/2,2.2])}
function supermarket(cx,cz){shell(cx,cz,20,14,5,0xe9eef2,-1,5);sign('SUPERMARKET',9,2,'#2f8a45',cx,8.5,cz);
 shelf(cx+2,cz-3.5,9,1,0xd9892b);shelf(cx+2,cz,9,1,0x4b9a5a);shelf(cx+2,cz+3.5,9,1,0xc0392b);scene.add(box(1.2,1.1,6,0x2f78b5,cx-7,.85,cz));boxes.push([cx-7.6,cx-6.4,cz-3,cz+3,1.4]);
 zones.push({x:cx-9,z:cz-2,r:1.9,l:function(){return 'Buy groceries $30 (+40 HP)'},f:function(){if(money>=30){money-=30;heal(40);toast('Groceries! +40 HP')}else toast('Not enough money')}},
 {x:cx-9,z:cz+2,r:1.9,l:function(){return 'Buy energy drink $12 (+15 HP)'},f:function(){if(money>=12){money-=12;heal(15);toast('Energy! +15 HP')}else toast('Not enough money')}})}
function clothing(cx,cz){shell(cx,cz,14,12,4.5,0xf3e6f0,-1,4);sign('CLOTHES',7,1.8,'#a0407a',cx,7.5,cz);
 for(var i=0;i<3;i++){scene.add(box(.1,1.8,3,0x444444,cx+3,1.2,cz-3+i*3),box(.5,1.2,2.6,[0xe05050,0x4a6ae0,0x50c070][i],cx+3,1.5,cz-3+i*3));boxes.push([cx+2.7,cx+3.3,cz-4.5+i*3,cz-1.5+i*3,2.2])}
 zones.push({x:cx-3,z:cz,r:3,l:function(){return 'New outfit $40 (random shirt)'},f:function(){if(money>=40){money-=40;setShirt(shirtCols[Math.floor(Math.random()*shirtCols.length)]);toast('Nice new shirt!')}else toast('Not enough money')}})}
function pharmacy(cx,cz){shell(cx,cz,14,12,4.5,0xe8f5ee,1,4);sign('PHARMACY',8,1.8,'#2a9d6a',cx,7.5,cz);scene.add(box(1,1.1,6,0x2a9d6a,cx-2,.85,cz));boxes.push([cx-2.5,cx-1.5,cz-3,cz+3,1.4]);
 zones.push({x:cx+3,z:cz,r:3,l:function(){return 'Buy medkit $50 (+60 HP)'},f:function(){if(money>=50){money-=50;heal(60);toast('Medkit used! +60 HP')}else toast('Not enough money')}})}
function school(cx,cz){var sx=cx-6;shell(sx,cz,20,22,8,0xe7c27a,1,6);sign('SCHOOL',8,2,'#8a5a1a',sx,11.5,cz);
 for(var r=0;r<3;r++)for(var c=0;c<2;c++){var dx=sx-6+c*5,dz=cz-6+r*6;scene.add(box(1.6,.9,.9,0x9a7a4a,dx,.75,dz));boxes.push([dx-.8,dx+.8,dz-.45,dz+.45,1.2])}
 scene.add(box(.1,1.6,5,0x2f5f45,sx-9.6,2.2,cz),box(13,.05,33,0x6fb860,cx+11.5,.27,cz));
 scene.add(box(4,.15,.15,0xc0392b,cx+13,3,cz-6),box(.15,3,.15,0x555555,cx+11,1.5,cz-6),box(.15,3,.15,0x555555,cx+15,1.5,cz-6));
 var sl=box(1.2,.15,4,0x3a6bc8,cx+9,1.3,cz+8);sl.rotation.x=.45;scene.add(sl);
 var fp=new THREE.Mesh(new THREE.CylinderGeometry(.08,.08,8,8),M(0xcccccc));fp.position.set(cx+16,4.2,cz-14);scene.add(fp,box(.1,.8,1.2,0xe05050,cx+16,7.6,cz-13.4));
 YARD={x0:cx+7,x1:cx+16,z0:cz-14,z1:cz+14}}
function addSmoke(x,y,z){for(var i=0;i<5;i++){var m=new THREE.Mesh(new THREE.SphereGeometry(.9,8,6),new THREE.MeshBasicMaterial({color:0x9aa0a8,transparent:true,opacity:.5}));scene.add(m);smoke.push({m:m,x:x,y:y,z:z,t:i*.8})}}
function factory(cx,cz,ds){shell(cx,cz,26,22,9,0x6b7280,ds,7);sign('FACTORY',8,2,'#444a55',cx,13,cz);
 [-6,6].forEach(function(dz){var ch=new THREE.Mesh(new THREE.CylinderGeometry(1.1,1.4,16,12),M(0x8a5a4a));ch.position.set(cx-ds*7,17,cz+dz);scene.add(ch);addSmoke(cx-ds*7,25.5,cz+dz)});
 for(var i=0;i<3;i++){var mx=cx-ds*4,mz=cz-7+i*7;scene.add(box(3,2.4,3,[0xe08a30,0x4a8ac8,0xc04a4a][i],mx,1.45,mz),box(1,.6,1,0x333333,mx,3,mz));boxes.push([mx-1.5,mx+1.5,mz-1.5,mz+1.5,2.7])}
 scene.add(box(2,.5,18,0x444a55,cx+ds*2,.55,cz));
 zones.push({x:cx+ds*8,z:cz,r:3.2,l:function(){return 'Work a shift (+$60)'},f:function(){var n=performance.now();if(n<fcool){toast('Take a short break first');return}fcool=n+25000;money+=60;hp=Math.max(1,hp-5);toast('Shift done: +$60')}})}
function busStation(cx,cz,ds,name){shell(cx,cz,22,16,5,0xcdd6e0,ds,6);sign(name,10,2,'#2f78b5',cx,8.5,cz);
 for(var i=0;i<3;i++){scene.add(box(.8,.5,3,0x6b4423,cx-ds*7,.5,cz-5+i*5));boxes.push([cx-ds*7-.4,cx-ds*7+.4,cz-6.5+i*5,cz-3.5+i*5,.8])}}
function shelter(p){var zz=p.z+(p.z<0?9:-9),sd=p.z<0?1.2:-1.2;scene.add(box(5.2,.2,2.6,0x2f5f9e,p.x,3,zz),box(.15,3,.15,0x555555,p.x-2.4,1.5,zz+sd),box(.15,3,.15,0x555555,p.x+2.4,1.5,zz+sd),box(5,2,.1,0xa9c9e0,p.x,1.8,zz+sd),box(3,.3,.7,0x6b4423,p.x,.55,zz));sign(p.n.toUpperCase(),5,1.2,'#2f5f9e',p.x,4.4,zz);return zz}
STOPS.forEach(function(p,i){if(!p.n)return;var al=Math.abs(p.x)===100;scene.add(box(al?2.4:12,.03,al?12:2.4,0xf2e8a0,p.x,.04,p.z));
 if(p.st){var sx=p.x<0?-91:91;waiting.push({i:i,x:p.x,z:p.z,pts:[[sx,p.z-3],[sx,p.z],[sx,p.z+3]]})}
 else{var zz=shelter(p);waiting.push({i:i,x:p.x,z:p.z,pts:[[p.x-1.2,zz],[p.x+1.2,zz]]})}});
[['5,3'],['4,3'],['6,3'],['3,3'],['6,6'],['3,6'],['7,5'],['2,5']].forEach(function(k){SPECIAL[k[0]]=houseBlock});
SPECIAL['3,5']=function(cx,cz){busStation(cx,cz,-1,'BUS STATION A')};SPECIAL['6,4']=function(cx,cz){busStation(cx,cz,1,'BUS STATION B')};
SPECIAL['3,4']=school;SPECIAL['6,5']=supermarket;SPECIAL['5,6']=clothing;SPECIAL['4,6']=pharmacy;
SPECIAL['7,7']=function(cx,cz){factory(cx,cz,-1)};SPECIAL['8,7']=function(cx,cz){factory(cx,cz,-1)};SPECIAL['7,8']=function(cx,cz){factory(cx,cz,-1)};SPECIAL['2,7']=function(cx,cz){factory(cx,cz,1)};


// ---- world: sea, islands, harbour, cemetery, airport, bank, petrol station, gun shop, futuristic home
var bank=0,bankLock=0,wown=[true,false,false,false,false,false,false,false,false,false],mapR=280,fishCool=0,bankCool=0;
var ISL=[{x:-300,z:650,r:55,chest:1500},{x:-100,z:800,r:55,chest:2500},{x:150,z:950,r:55,chest:4000},{x:450,z:700,r:110,zombie:1}];
function isWater(x,z){if(Math.abs(x)<=350&&Math.abs(z)<=350)return false;
 if(Math.abs(x)<=6&&z>350&&z<=420)return false;if(Math.abs(x+40)<=4&&z>350&&z<=395)return false;
 for(var i=0;i<ISL.length;i++){var s=ISL[i],dx=x-s.x,dz=z-s.z,rr=s.r+6;if(dx*dx+dz*dz<rr*rr)return false;if(Math.abs(dx)<=3&&z>s.z-s.r-12&&z<s.z-s.r+8)return false}return true}
function ground(x,z){if(onBlock(x,z))return .25;return isWater(x,z)?-.8:0}
Object.keys(MODELS).forEach(function(k){MODELS[k].price=0});
MODELS.jeep={n:'Jeep',price:0,col:0x5a7d3a,sc:[1.12,1.3,1.05],top:36,acc:18,turn:1.8};
var sea=new THREE.Mesh(new THREE.PlaneGeometry(9000,9000).rotateX(-Math.PI/2),new THREE.MeshLambertMaterial({color:0x2f78b5}));sea.position.y=-.3;scene.add(sea);
var sandp=new THREE.Mesh(new THREE.PlaneGeometry(730,730).rotateX(-Math.PI/2),M(0xe2d29a));sandp.position.y=-.12;scene.add(sandp);
// harbour
scene.add(box(14,.03,90,0x2f343b,0,.01,307),box(90,.03,26,0x3a3f48,20,.01,335),box(12,.3,70,0x8a6a3a,0,-.05,385),box(8,.3,45,0x8a6a3a,-40,-.05,372.5));
sign('HARBOUR',9,2,'#2f5f9e',0,8,352);sign('FISHING PIER',9,2,'#1d6a8a',-40,6,352);
for(var i=0;i<8;i++){var kx=45+(i%4)*8,kz=322+Math.floor(i/4)*5;scene.add(box(6,2.6,2.4,[0xc0392b,0x2f78b5,0xd9892b,0x4b9a5a][(i+Math.floor(i/4))%4],kx,1.55,kz));boxes.push([kx-3,kx+3,kz-1.2,kz+1.2,2.8])}
[-1,1].forEach(function(sd){var cx2=sd*70;scene.add(box(1,18,1,0xd9892b,cx2-3,9,300),box(1,18,1,0xd9892b,cx2+3,9,300),box(8,1,1,0xd9892b,cx2,18,300));boxes.push([cx2-3.6,cx2+3.6,299.5,300.5,18])});
shell(-75,330,22,14,6,0x8a8f99,1,5);sign('HARBOUR OFFICE',10,2,'#444a55',-75,9.5,330);
[[-12,365],[-12,388]].forEach(function(p){scene.add(box(3,.9,7,0xc0392b,p[0],-.1,p[1]),box(1.6,1.1,2,0xffffff,p[0],.8,p[1]+.8))});
[[-48,380],[-33,372]].forEach(function(p){scene.add(box(2.6,.8,5.5,0x2f78b5,p[0],-.1,p[1]),box(1.4,1,1.8,0xffffff,p[0],.7,p[1]+.6))});
zones.push({x:-40,z:392,r:3.2,l:function(){return 'Fish here (watch out for sharks)'},f:function(){var n=performance.now();if(n<fishCool){toast('Wait a moment');return}fishCool=n+3000;var r=Math.random();
 if(r<.5){money+=20;toast('You caught a fish! +$20')}else if(r<.75){money+=75;toast('A big fish! +$75')}else if(r<.9)toast('Just an old boot...');else toast('A shark snapped your line!')}});
// islands
ISL.forEach(function(s,i){var rr=s.r;
 scene.add(new THREE.Mesh(new THREE.CylinderGeometry(rr+6,rr+8,2.4,40),M(0xe2d29a)).translateX(s.x).translateY(-1.2).translateZ(s.z),new THREE.Mesh(new THREE.CylinderGeometry(rr-2,rr,.1,40),M(s.zombie?0x4a5a3a:0x4f9a4a)).translateX(s.x).translateZ(s.z));
 scene.add(box(6,.25,22,0x8a6a3a,s.x,-.1,s.z-rr-1));
 for(var k=0;k<(s.zombie?10:8);k++){var a=hash(i*20+k,1,70)*6.28,r2=Math.sqrt(hash(i*20+k,2,70))*(rr-12),px=s.x+Math.cos(a)*r2,pz=s.z+Math.sin(a)*r2;
  var tr=new THREE.Mesh(new THREE.CylinderGeometry(.2,.3,5,6),M(0x7a5230)),lf=new THREE.Mesh(new THREE.SphereGeometry(2,8,6),M(s.zombie?0x3a4a2a:0x2f8a45));tr.position.set(px,2.5,pz);lf.scale.y=.45;lf.position.set(px,5.2,pz);scene.add(tr,lf);boxes.push([px-.4,px+.4,pz-.4,pz+.4,5])}
 if(s.chest){var cx2=s.x+rr*.3,cz2=s.z+rr*.15,lid=box(1.7,.35,1.1,0xd4af37,cx2,1.15,cz2);scene.add(box(1.6,1,1,0x7a4a1a,cx2,.5,cz2),lid);boxes.push([cx2-.9,cx2+.9,cz2-.6,cz2+.6,1.4]);sign('TREASURE ISLAND',9,2,'#8a5a1a',s.x,12,s.z);
  zones.push({x:cx2,z:cz2,r:3,l:function(){return s.done?'The chest is empty':'Open the treasure chest (+$'+s.chest+')'},f:function(){if(s.done){toast('Already looted. It refills later.');return}s.done=1;money+=s.chest;lid.rotation.x=-1;toast('Treasure! +$'+s.chest);setTimeout(function(){s.done=0;lid.rotation.x=0},300000)}})}
 else{sign('ZOMBIE ISLAND',10,2,'#3a5a2a',s.x,12,s.z);for(var k=0;k<6;k++){var qx=s.x+(hash(k,3,71)-.5)*120,qz=s.z+(hash(k,4,71)-.5)*120;scene.add(box(4,3+k%3,.6,0x6a6a72,qx,1.8,qz));boxes.push([qx-2,qx+2,qz-.3,qz+.3,4])}}});
// cemetery
(function(){var cx=-290,cz=-250;scene.add(box(62,.05,62,0x3b4a3a,cx,.0,cz));
 [[cx,cz-31,62,.3],[cx-17,cz+31,28,.3],[cx+17,cz+31,28,.3]].forEach(function(f){scene.add(box(f[2],1.4,f[3],0x2a2a2a,f[0],.7,f[1]));boxes.push([f[0]-f[2]/2,f[0]+f[2]/2,f[1]-.2,f[1]+.2,1.5])});
 [[cx-31,cz],[cx+31,cz]].forEach(function(f){scene.add(box(.3,1.4,62,0x2a2a2a,f[0],.7,f[1]));boxes.push([f[0]-.2,f[0]+.2,f[1]-31,f[1]+31,1.5])});
 for(var i=0;i<5;i++)for(var j=0;j<5;j++){var x=cx-20+i*10+(hash(i,j,80)-.5)*3,z=cz-20+j*9+(hash(j,i,81)-.5)*2;scene.add(box(1,1.6,.35,0x9aa0a6,x,.8,z));if((i+j)%3===0)scene.add(box(.15,1,.15,0x9aa0a6,x,2.1,z),box(.7,.15,.15,0x9aa0a6,x,2.3,z));boxes.push([x-.5,x+.5,z-.25,z+.25,1.7])}
 for(var i=0;i<6;i++){var tx=cx-24+i*10,tz=cz+(i%2?24:-26);var t=new THREE.Mesh(new THREE.CylinderGeometry(.2,.35,6,6),M(0x2a2018));t.position.set(tx,3,tz);scene.add(t,box(2.4,.15,.15,0x2a2018,tx,5,tz),box(.15,.15,2,0x2a2018,tx,4,tz))}
 shell(cx+20,cz-20,8,8,4,0x6a6a72,-1,2.6);sign('CEMETERY',8,2,'#2a2a2a',cx,5,cz+31)})();
// airport
(function(){var rx=310;scene.add(box(24,.05,330,0x30343b,rx,.03,0),box(50,.04,14,0x30343b,285,.03,0));
 for(var z=-150;z<=150;z+=20)scene.add(box(.8,.06,8,0xffffff,rx,.07,z));
 shell(268,-70,22,30,7,0xdfe6ee,1,6);sign('AIRPORT',9,2,'#2f5f9e',268,10.5,-70);shell(268,70,24,22,9,0x8a8f99,1,12);sign('HANGAR',7,1.8,'#444a55',268,12.5,70);
 scene.add(box(4,22,4,0xdddddd,262,11,12),box(6,3,6,0x7fd0ff,262,23.5,12));boxes.push([260,264,10,14,22]);
 var hp2=new THREE.Mesh(new THREE.CylinderGeometry(7,7,.05,24),M(0x444a55));hp2.position.set(268,.06,130);scene.add(hp2);sign('HELIPAD',6,1.5,'#444a55',268,3,130);
 [[292,-25],[292,15]].forEach(function(p){scene.add(box(1.4,1.3,6.5,0xf0f4f8,p[0],1.3,p[1]),box(1.7,.15,11,0xf0f4f8,p[0],1.45,p[1]),box(.12,1.6,1.1,0x3a6bc8,p[0],2.2,p[1]+3));boxes.push([p[0]-5.5,p[0]+5.5,p[1]-3.3,p[1]+3.3,2.5])})})();
// petrol station
function petrol(cx,cz){scene.add(box(18,.4,10,0xd9d9d9,cx,5.2,cz),box(18.2,.3,.2,0xc0392b,cx,4.9,cz-5),box(18.2,.3,.2,0xc0392b,cx,4.9,cz+5));
 [[-8,-4],[8,-4],[-8,4],[8,4]].forEach(function(p){scene.add(box(.5,5,.5,0x888e99,cx+p[0],2.7,cz+p[1]));boxes.push([cx+p[0]-.3,cx+p[0]+.3,cz+p[1]-.3,cz+p[1]+.3,5])});
 sign('PETROL',6,1.6,'#c0392b',cx,7.4,cz);
 [-4,4].forEach(function(dx){scene.add(box(.8,1.7,1.2,0xc0392b,cx+dx,1.1,cz),box(.6,.4,1,0x222222,cx+dx,1.7,cz));boxes.push([cx+dx-.5,cx+dx+.5,cz-.7,cz+.7,2]);
  zones.push({x:cx+dx,z:cz,r:4.8,veh:true,l:function(){return 'Fill the tank ($'+Math.ceil((100-(C.fuel||0))*.5)+')'},f:refuel})})}
function refuel(){if(!inCar||!C.needsFuel){toast('Drive a petrol vehicle up to the pump');return}var miss=100-C.fuel,cost=Math.ceil(miss*.5);
 if(miss<1){toast('The tank is already full');return}if(money>=cost){money-=cost;C.fuel=100;C.fuelOut=false;toast('Tank full. Paid $'+cost)}else{var u=Math.floor(money*2);money-=Math.ceil(u/2);C.fuel+=u;toast(u>0?'Not enough money. Partial fill +'+u+'%':'No money for petrol')}}
// gun shop
function gunshop(cx,cz){shell(cx,cz,24,16,5,0x3a3f48,-1,5);sign('GUN SHOP',8,2,'#222222',cx,8.5,cz);
 var it=[[1,'Knife'],[2,'Bat'],[3,'Pistol'],[4,'UMP'],[5,'M4'],[6,'AK-47'],[7,'Rocket Launcher'],[8,'Bomb'],[9,'Time Bomb']];
 it.forEach(function(g,k){var back=k<5,x=back?cx+9:cx+3,z=cz+(back?(k-2)*3.2:(k-5-1.5)*3.2);scene.add(box(.5,.9,1.6,0x555a66,x+(back?.8:0),.7,z));boxes.push([x+(back?.5:-.25),x+(back?1.1:.25),z-.8,z+.8,1.2]);
  zones.push({x:x-(back?1.3:0),z:z,r:1.6,l:function(){return wown[g[0]]?'Select '+g[1]+' (you have it)':'Take the '+g[1]+' (free)'},f:function(){wown[g[0]]=true;wi=g[0];toast('You got the '+g[1]+'. Select with number keys or the Gun button.')}})})}
// bank with automatic doors and security
var bankDoorL=[0,0,0,0,3.4],bankDoorR=[0,0,0,0,3.4],bankDoorMeshes=[],bankX=0,bankZ=0;
function bankBuild(cx,cz){bankX=cx+12;bankZ=cz;shell(cx,cz,24,20,7,0xe6dcc0,1,6);sign('BANK',6,2,'#b8860b',cx,10.5,cz);
 var gm=new THREE.MeshLambertMaterial({color:0x7fd0ff,transparent:true,opacity:.5});[0,1].forEach(function(k){var m=new THREE.Mesh(new THREE.BoxGeometry(.3,3.4,3),gm);m.position.set(cx+12,1.95,cz);scene.add(m);bankDoorMeshes.push(m)});boxes.push(bankDoorL,bankDoorR);
 scene.add(box(1.2,1.1,10,0xb8860b,cx+2,.85,cz),box(.1,1.3,10,0x9ec7e0,cx+2,1.8,cz));boxes.push([cx+1.4,cx+2.6,cz-5,cz+5,1.4]);
 [-5,5].forEach(function(dz){scene.add(box(1.2,2,1,0x2a3a5a,cx-10,1.25,cz+dz),box(.1,.7,.8,0x22aaff,cx-9.45,1.6,cz+dz));boxes.push([cx-10.6,cx-9.4,cz+dz-.5,cz+dz+.5,2.3])});
 scene.add(box(3.2,3,3.2,0x8a8f99,cx-8,1.6,cz),box(1.6,.5,.8,0xd4af37,cx-8,3.3,cz));boxes.push([cx-9.6,cx-6.4,cz-1.6,cz+1.6,3.2]);
 var red=new THREE.MeshBasicMaterial({color:0xff2020});[.6,1.2,1.8].forEach(function(y){var l=new THREE.Mesh(new THREE.BoxGeometry(.04,.04,8),red);l.position.set(cx-4.5,y,cz);scene.add(l)});
 [[cx+11,cz-9],[cx+11,cz+9]].forEach(function(p){scene.add(box(.3,.3,.5,0x222222,p[0],6,p[1]));var e=new THREE.Mesh(new THREE.SphereGeometry(.1,6,5),red);e.position.set(p[0]-.2,6,p[1]);scene.add(e)});
 zones.push({x:cx-8.5,z:cz-5,r:2.4,l:function(){return 'ATM: deposit all cash ($'+money+')'},f:function(){if(money<=0){toast('You have no cash');return}bank+=money;toast('Deposited $'+money+'. Bank balance $'+bank);money=0}},
 {x:cx-8.5,z:cz+5,r:2.4,l:function(){return 'ATM: withdraw $500 (balance $'+bank+')'},f:function(){var a=Math.min(500,bank);if(a<=0){toast('Your bank balance is empty');return}bank-=a;money+=a;toast('Withdrew $'+a+'. Balance $'+bank)}},
 {x:cx-5.3,z:cz,r:2.4,l:function(){return 'Break into the vault (risky!)'},f:function(){var n=performance.now();if(n<bankCool){toast('The vault is still locked down');return}bankCool=n+60000;bankLock=8;setStars(4);
  if(Math.random()<.4){money+=6000;toast('You cracked the vault! +$6000. The alarm is ringing!')}else toast('Alarm! Security lockdown and the police are coming!')}})}
// futuristic player home
function house(cx,cz){var hx=cx,hz=cz-1.5,w=26,d=17,h=5.5;shell(hx,hz,w,d,h,0xf4f7fb,-1,6);
 var neon=new THREE.MeshBasicMaterial({color:0x00e5ff}),pk=new THREE.MeshBasicMaterial({color:0xff4fd8});
 function nb(w2,h2,d2,m,x,y,z){var q=new THREE.Mesh(new THREE.BoxGeometry(w2,h2,d2),m);q.position.set(x,y,z);scene.add(q)}
 nb(w+.8,.12,.12,neon,hx,h+.8,hz-d/2-.3);nb(w+.8,.12,.12,neon,hx,h+.8,hz+d/2+.3);nb(.12,.12,d+.8,pk,hx-w/2-.3,h+.8,hz);nb(.12,.12,d+.8,pk,hx+w/2+.3,h+.8,hz);nb(.12,4,.12,neon,hx-w/2-.2,2.2,hz-3.3);nb(.12,4,.12,neon,hx-w/2-.2,2.2,hz+3.3);
 var gl=new THREE.Mesh(new THREE.BoxGeometry(16,3.6,10),new THREE.MeshLambertMaterial({color:0x7fe8ff,transparent:true,opacity:.45}));gl.position.set(hx+3,h+2.6,hz);scene.add(gl,box(16.4,.3,10.4,0x23303f,hx+3,h+4.55,hz));
 [-6,-2,2,6].forEach(function(dx){var sp=box(3,.1,1.8,0x1d3b8a,hx+dx-4,h+1.2,hz+4.5);sp.rotation.x=-.4;scene.add(sp)});
 sign('SMART HOME',8,2,'#0a2a3a',hx,h+7.4,hz);
 scene.add(box(3.4,.6,2.4,0x1a2a4a,hx+10,.65,hz-5),box(1,.2,1.6,0xffffff,hx+11.8,1,hz-5),box(4,.7,1.4,0x3a3a4a,hx-2,.65,hz+6.5),box(3.2,1.8,.1,0x22aaff,hx-2,1.9,hz+8.1),box(4,1.1,1.4,0xdfe6ee,hx+6,.85,hz+6),box(1.2,2.4,1,0xcfd8dc,hx+11.5,1.45,hz+6.5));
 var cyl=new THREE.Mesh(new THREE.CylinderGeometry(.8,.8,.9,16),M(0x2a3a5a));cyl.position.set(hx+3,.7,hz+1);var holo=new THREE.Mesh(new THREE.SphereGeometry(.45,12,10),new THREE.MeshBasicMaterial({color:0x00e5ff,transparent:true,opacity:.6}));holo.position.set(hx+3,1.9,hz+1);scene.add(cyl,holo);
 boxes.push([hx+8.3,hx+11.7,hz-6.2,hz-3.8,1.2],[hx-4,hx,hz+5.8,hz+7.2,1.1],[hx+4,hx+8,hz+5.3,hz+6.7,1.4],[hx+10.9,hx+12.1,hz+6,hz+7,2.5],[hx+2.2,hx+3.8,hz+.2,hz+1.8,1.2]);
 zones.push({x:hx+7,z:hz-5,r:2.8,l:function(){return 'Sleep until morning'},f:function(){clock=0;hp=100;toast('You slept well. Health restored.')}},
 {x:hx-2,z:hz+4,r:2.2,l:function(){return 'Watch TV (+5 HP)'},f:function(){heal(5);toast('Relaxing... +5 HP')}},
 {x:hx+9,z:hz+5,r:2.4,l:function(){return 'Eat from the fridge (+10 HP)'},f:function(){heal(10);toast('Snack time! +10 HP')}})}
SPECIAL['5,3']=petrol;SPECIAL['4,3']=bankBuild;SPECIAL['6,3']=gunshop;

// textures and materials
function tex(lit){var c=document.createElement('canvas');c.width=c.height=128;var x=c.getContext('2d');x.fillStyle=lit?'#000':'#f4f1ea';x.fillRect(0,0,128,128);
 for(var r=0;r<4;r++)for(var q=0;q<4;q++){var wx=q*32+6,wy=r*32+7;if(lit){if(Math.random()<.4){x.fillStyle=Math.random()<.5?'#ffd98a':'#fff2c8';x.fillRect(wx,wy,20,16)}}else{x.fillStyle='#35465a';x.fillRect(wx,wy,20,16)}}
 var t=new THREE.CanvasTexture(c);t.wrapS=t.wrapT=THREE.RepeatWrapping;return t}
var tw=tex(false),tl=tex(true),bmats=[0xd8d2c4,0xb9c4cf,0xc9a98f,0x9fb0a0,0xe0e0e0,0xa89bb0].map(function(c){return new THREE.MeshLambertMaterial({color:c,map:tw,emissive:0xffffff,emissiveMap:tl,emissiveIntensity:0})});
function bgeo(w,h,d){var g=new THREE.BoxGeometry(w,h,d),uv=g.attributes.uv;
 for(var i=0;i<24;i++){var f=Math.floor(i/4),u=uv.getX(i),v=uv.getY(i);
  if(f<2){uv.setXY(i,u*d/12,v*h/14)}else if(f<4){uv.setXY(i,.01,.01)}else{uv.setXY(i,u*w/12,v*h/14)}}
 return g}

// city
var treePts=[],bl=new THREE.InstancedMesh(new THREE.BoxGeometry(36,.25,36).translate(0,.125,0),new THREE.MeshLambertMaterial({color:0xffffff}),N*N),dm=new THREE.Object3D(),cc=new THREE.Color(),bi=0;
for(var i=0;i<N;i++)for(var j=0;j<N;j++){
 var cx=rc(i)+CELL/2,cz=rc(j)+CELL/2,park=hash(i,j,3)<.14&&(i+j)%3!==0&&!SPECIAL[i+','+j];
 dm.position.set(cx,0,cz);dm.updateMatrix();bl.setMatrixAt(bi,dm.matrix);bl.setColorAt(bi++,cc.set(park?0x66a85b:0xbab7b0));
 if(SPECIAL[i+','+j]){SPECIAL[i+','+j](cx,cz);continue} if(park){for(var t=0;t<9;t++){var tx=cx+(hash(i*9+t,j,4)-.5)*30,tz=cz+(hash(i*9+t,j,5)-.5)*30;treePts.push([tx,tz]);boxes.push([tx-.5,tx+.5,tz-.5,tz+.5,6])}continue}
 var dist=Math.hypot(cx,cz)/HALF;
 for(var a=0;a<2;a++)for(var b=0;b<2;b++){var s=i*100+j*10+a*2+b;if(hash(s,1,6)<.12)continue;
  var w=10+hash(s,2,6)*3.5,d=10+hash(s,3,6)*3.5,hh=9+hash(s,4,6)*(16+80*Math.pow(1-dist,2)),bx=cx+(a?7:-7),bz=cz+(b?7:-7);
  var m=new THREE.Mesh(bgeo(w,hh,d),bmats[Math.floor(hash(s,5,6)*6)]);m.position.set(bx,.25+hh/2,bz);scene.add(m);boxes.push([bx-w/2,bx+w/2,bz-d/2,bz+d/2,hh+.25])}}
scene.add(bl);
var tt=new THREE.InstancedMesh(new THREE.CylinderGeometry(.2,.28,2.6).translate(0,1.3,0),M(0x6b4423),treePts.length),tf=new THREE.InstancedMesh(new THREE.SphereGeometry(2.1,8,6).translate(0,4,0),M(0x2f8a45),treePts.length);
treePts.forEach(function(p,k){dm.position.set(p[0],.25,p[1]);dm.scale.setScalar(.8+hash(k,1,8)*.6);dm.updateMatrix();tt.setMatrixAt(k,dm.matrix);tf.setMatrixAt(k,dm.matrix)});dm.scale.setScalar(1);scene.add(tt,tf);
// dashes + lights
var dashes=[],poles=[];
for(var r=0;r<=N;r++)for(var s=0;s<N;s++)for(var q=0;q<4;q++){var along=rc(s)+CELL/2+(q-1.5)*8;dashes.push([along,rc(r),0],[rc(r),along,1])}
var dI=new THREE.InstancedMesh(new THREE.BoxGeometry(3,.03,.3),M(0xe8e2b0),dashes.length);
dashes.forEach(function(p,k){dm.position.set(p[2]?p[0]:p[0],.03,p[2]?p[1]:p[1]);dm.rotation.y=p[2]?Math.PI/2:0;dm.updateMatrix();dI.setMatrixAt(k,dm.matrix)});dm.rotation.y=0;scene.add(dI);
for(var r=0;r<=N;r++)for(var s=0;s<=N;s++){poles.push([rc(r)+8,rc(s)+8],[rc(r)-8,rc(s)-8])}
var pI=new THREE.InstancedMesh(new THREE.CylinderGeometry(.1,.12,6).translate(0,3,0),M(0x44484f),poles.length),lampM=new THREE.MeshBasicMaterial({color:0x777777}),lI=new THREE.InstancedMesh(new THREE.SphereGeometry(.4,8,6).translate(0,6.2,0),lampM,poles.length);
poles.forEach(function(p,k){dm.position.set(p[0],.25,p[1]);dm.updateMatrix();pI.setMatrixAt(k,dm.matrix);lI.setMatrixAt(k,dm.matrix)});scene.add(pI,lI);

// people
function human(shirt,pants,skin,hair){var g=new THREE.Group(),o={g:g,lL:new THREE.Group(),lR:new THREE.Group(),aL:new THREE.Group(),aR:new THREE.Group()};
 o.lL.position.set(-.14,.9,0);o.lR.position.set(.14,.9,0);
 [o.lL,o.lR].forEach(function(l){l.add(box(.22,.9,.26,pants,0,-.45,0));l.add(box(.24,.12,.34,0x222222,0,-.86,-.04));g.add(l)});
 g.add(box(.56,.72,.32,shirt,0,1.26,0));
 var h=new THREE.Mesh(new THREE.SphereGeometry(.17,14,10),M(skin));h.position.y=1.82;g.add(h);
 var hr=new THREE.Mesh(new THREE.SphereGeometry(.185,14,8,0,Math.PI*2,0,Math.PI*.55),M(hair));hr.position.y=1.84;hr.rotation.x=-.25;g.add(hr);
 g.add(box(.05,.05,.03,0x222222,-.06,1.84,-.16),box(.05,.05,.03,0x222222,.06,1.84,-.16));
 [[o.aL,-.37],[o.aR,.37]].forEach(function(a){a[0].position.set(a[1],1.54,0);a[0].add(box(.16,.66,.18,shirt,0,-.31,0));a[0].add(box(.14,.14,.16,skin,0,-.7,0));g.add(a[0])});
 scene.add(g);return o}
function swing(o,ph,amt){var s=Math.sin(ph)*amt*.9;o.lL.rotation.x=s;o.lR.rotation.x=-s;o.aL.rotation.x=-s*.8;o.aR.rotation.x=s*.8}
var shirts=[0xb5483a,0x3a6bb5,0x4b9a5a,0xd0a23a,0x8a4fb0,0x333333,0xe0e0e0],skins=[0xf0c9a0,0xd9a577,0xa87650,0x7a5233,0xf5d6b8],hairs=[0x2a1c10,0x6b4a2a,0x111111,0xc8a050,0x777777];
var me=human(0x111111,0xf6f1e3,0xf2d7c0,0x050505);
var peds=[];for(var i=0;i<30;i++){var o=human(shirts[i%7],[0x2c3e63,0x4a4a4a,0x6b5a3a][i%3],skins[i%5],hairs[(i*3)%5]);
 var ax=i%2,r=Math.floor(hash(i,1,20)*(N+1)),side=hash(i,2,20)<.5?-1:1;peds.push({o:o,ax:ax,lat:rc(r)+side*9,s:(hash(i,3,20)-.5)*HALF*2,dir:hash(i,4,20)<.5?-1:1,ph:hash(i,5,20)*6,sp:1.1+hash(i,6,20)*.5})}

// cars
function car(color){var g=new THREE.Group();g.add(box(2,.7,4.2,color,0,.65,0),box(1.7,.6,2.1,color,0,1.25,.2));
 g.add(box(1.72,.45,1.9,0x9ec7e0,0,1.28,.2));
 [[-.95,1.3],[.95,1.3],[-.95,-1.3],[.95,-1.3]].forEach(function(w){var t=new THREE.Mesh(new THREE.CylinderGeometry(.38,.38,.3,12),M(0x1a1a1a));t.rotation.z=Math.PI/2;t.position.set(w[0],.38,w[1]);g.add(t)});
 g.add(box(.4,.2,.05,0xfff5b0,-.6,.7,-2.12),box(.4,.2,.05,0xfff5b0,.6,.7,-2.12),box(.4,.15,.05,0xc02020,-.6,.7,2.12),box(.4,.15,.05,0xc02020,.6,.7,2.12));scene.add(g);return g}
var tcols=[0xc83a3a,0x3a6bc8,0xeeeeee,0x2a2a2a,0x3aa05a,0xc8c8d0,0x8a4fb0],traffic=[];
for(var i=0;i<14;i++){var ax=i%2,r=1+Math.floor(hash(i,1,30)*(N-1)),dir=hash(i,2,30)<.5?-1:1;traffic.push({g:car(tcols[i%7]),ax:ax,r:r,dir:dir,s:(hash(i,3,30)-.5)*HALF*2,v:0,top:7+hash(i,4,30)*4})}
var C={x:3.5,z:14,h:0,v:0,g:car(0xf2c230)};C.g.position.set(C.x,0,C.z);C.top=27;C.acc=15;C.turn=1.9;C.rad=2.1;C.cd=8;C.t='car';C.alt=0;C.fv=0;C.vy=0;C.noG=false;C.kind='';C.fuel=100;C.needsFuel=true;C.engOff=false;C.fuelOut=false;

// state
var P={x:23,z:26,y:.25,vx:0,vz:0,vy:0,on:true},yaw=1.57,pitch=.08,face=1.57,walk=0,inCar=false,sprint=false,keys={},joy=null,look=null,locked=false,mouseDown=false,clock=.2,lastE=0;
var clkEl=document.getElementById('clk'),spdEl=document.getElementById('spd'),hint=document.getElementById('hint'),startEl=document.getElementById('start'),joyEl=document.getElementById('joy'),knob=joyEl.firstChild;
function begin(){startEl.style.display='none';if(!touch){try{R.domElement.requestPointerLock()}catch(e){}}}
startEl.addEventListener('click',begin);
document.addEventListener('pointerlockchange',function(){locked=document.pointerLockElement===R.domElement});
addEventListener('keydown',function(e){var k=e.key.toLowerCase();keys[k]=1;if(k==='e')toggleCar();if(e.key===' '||e.key.indexOf('Arrow')===0)e.preventDefault()});
addEventListener('keyup',function(e){keys[e.key.toLowerCase()]=0});
addEventListener('mousemove',function(e){if(locked||mouseDown){yaw-=e.movementX*.0025;pitch=Math.max(-.5,Math.min(.9,pitch-e.movementY*.0025))}});
addEventListener('mousedown',function(){mouseDown=true});addEventListener('mouseup',function(){mouseDown=false});
function btn(id,dn,up){var b=document.getElementById(id);b.addEventListener('pointerdown',function(e){e.stopPropagation();e.preventDefault();dn()});['pointerup','pointercancel','pointerleave'].forEach(function(n){b.addEventListener(n,function(e){e.stopPropagation();if(up)up()})})}
btn('bj',function(){keys[' ']=1},function(){keys[' ']=0});btn('bs',function(){sprint=!sprint});btn('bd',toggleCar);
addEventListener('pointerdown',function(e){if(e.pointerType==='mouse'||startEl.style.display!=='none'||e.target.tagName==='BUTTON')return;
 if(e.clientX<W*.5&&!joy){joy={id:e.pointerId,ox:e.clientX,oy:e.clientY,dx:0,dy:0};joyEl.style.display='block';joyEl.style.left=e.clientX+'px';joyEl.style.top=e.clientY+'px';knob.style.transform=''}
 else if(!look)look={id:e.pointerId,x:e.clientX,y:e.clientY}});
addEventListener('pointermove',function(e){if(joy&&e.pointerId===joy.id){var dx=e.clientX-joy.ox,dy=e.clientY-joy.oy,d=Math.hypot(dx,dy);if(d>50){dx=dx/d*50;dy=dy/d*50}joy.dx=dx/50;joy.dy=dy/50;knob.style.transform='translate('+dx+'px,'+dy+'px)'}
 if(look&&e.pointerId===look.id){yaw-=(e.clientX-look.x)*.006;pitch=Math.max(-.5,Math.min(.9,pitch-(e.clientY-look.y)*.006));look.x=e.clientX;look.y=e.clientY}});
function up(e){if(joy&&e.pointerId===joy.id){joy=null;joyEl.style.display='none'}if(look&&e.pointerId===look.id)look=null}
addEventListener('pointerup',up);addEventListener('pointercancel',up);
function near(){return Math.hypot(P.x-C.x,P.z-C.z)<4.5}
function toggleCar(){var n=performance.now();if(n-lastE<300||startEl.style.display!=='none')return;lastE=n;if(riding){leaveBus();return}if(!inCar){var nb=nearBus();if(nb){boardBus(nb);return}if(!near()&&!riding){var tc=nearTraffic();if(tc){stealCar(tc);return}}}if(inCar&&(C.alt||0)>3){toast('Land before getting out');return}
 if(inCar){inCar=false;P.x=C.x+Math.cos(C.h)*3;P.z=C.z-Math.sin(C.h)*3;P.y=ground(P.x,P.z);P.vx=P.vz=0;me.g.visible=true;spdEl.style.display='none'}
 else if(near()){inCar=true;me.g.visible=false;spdEl.style.display='block';hint.style.display='none'}}
function push(o,r){var hit=false;for(var i=0;i<boxes.length;i++){var b=boxes[i];if(o.x<b[0]-r||o.x>b[1]+r||o.z<b[2]-r||o.z>b[3]+r)continue;
 var qx=Math.max(b[0],Math.min(o.x,b[1])),qz=Math.max(b[2],Math.min(o.z,b[3])),dx=o.x-qx,dz=o.z-qz,d2=dx*dx+dz*dz;
 if(d2<r*r){hit=true;if(d2>1e-6){var d=Math.sqrt(d2);o.x=qx+dx/d*r;o.z=qz+dz/d*r}else{var l=o.x-b[0],rr=b[1]-o.x,t=o.z-b[2],bt=b[3]-o.z,m=Math.min(l,rr,t,bt);if(m===l)o.x=b[0]-r;else if(m===rr)o.x=b[1]+r;else if(m===t)o.z=b[2]-r;else o.z=b[3]+r}}}return hit}
function angd(a){return Math.atan2(Math.sin(a),Math.cos(a))}

var sk=new THREE.Color(),DAY=new THREE.Color(0x8fcdf0),NIGHT=new THREE.Color(0x070d1c),DUSK=new THREE.Color(0xf09060);
function sky(){var a=clock*Math.PI*2,s=Math.sin(a),day=Math.max(0,Math.min(1,(s+.15)/.5)),dusk=Math.max(0,1-Math.abs(s)/.28);
 sk.copy(NIGHT).lerp(DAY,day).lerp(DUSK,dusk*.55);scene.background.copy(sk);scene.fog.color.copy(sk);
 hemi.intensity=.22+.75*day;sun.intensity=.1+.8*day;sun.position.set(Math.cos(a)*200,Math.max(30,s*200),80);
 var em=Math.max(0,Math.min(1,(.15-s)/.4));bmats.forEach(function(m){m.emissiveIntensity=em*.9});lampM.color.setRGB(.45+.55*em,.45+.4*em,.45+.05*em);
 var mins=Math.floor(((clock*24+6)%24)*60);clkEl.textContent=('0'+Math.floor(mins/60)).slice(-2)+':'+('0'+mins%60).slice(-2)}

// ---- gameplay systems
var hp=100,wanted=0,calm=0,down=null,phoneOpen=false,firing=false,wi=0,lastFire=-9,atk=0,toastT=0,hurtCool=0,curZ=null,cur=-1,codeBuf='',cmsg='';
var WEAPONS=[{n:'Hand',melee:1.7,dmg:15,cd:.45},{n:'Knife',melee:2,dmg:40,cd:.3},{n:'Bat',melee:2.6,dmg:60,cd:.55,bat:1},{n:'Pistol',dmg:25,cd:.35},{n:'UMP',dmg:14,cd:.075},{n:'M4',dmg:22,cd:.09},{n:'AK-47',dmg:20,cd:.1},{n:'Rocket Launcher',rpg:1,cd:1.6},{n:'Bomb',bomb:1,cd:1},{n:'Time Bomb',tbomb:1,cd:1}];
var toastEl=document.getElementById('toast'),bustEl=document.getElementById('bust'),monEl=document.getElementById('mon'),hpf=document.getElementById('hpf'),wanEl=document.getElementById('wan'),wpnEl=document.getElementById('wpn'),cr2=document.getElementById('cross2'),phoneEl=document.getElementById('phone'),scr=document.getElementById('pscr');
function toast(m){toastEl.textContent=m;toastEl.style.opacity=1;toastT=3.2}
function hurt(n){if(!down)hp-=n}
function isCar(t){return !!MODELS[t]||t==='car'}

// vehicles
function wheel(r,t){var w=new THREE.Mesh(new THREE.TorusGeometry(r,t,6,16),M(0x1a1a1a));w.rotation.y=Math.PI/2;return w}
function build0(type){var g=new THREE.Group(),a,b;
 if(type==='cycle'){a=wheel(.38,.05);b=wheel(.38,.05);a.position.set(0,.4,-.75);b.position.set(0,.4,.75);g.add(a,b,box(.06,.06,1.5,0xc0392b,0,.75,0),box(.5,.05,.05,0x222222,0,1.1,-.6),box(.1,.08,.3,0x222222,0,1.05,.35));C.top=9;C.acc=7;C.turn=2.6;C.rad=.8;C.cd=5.5}
 else if(type==='bike'){a=wheel(.4,.1);b=wheel(.4,.1);a.position.set(0,.42,-.8);b.position.set(0,.42,.8);g.add(a,b,box(.4,.5,1.4,0x1f2a44,0,.8,0),box(.35,.3,.6,0xd32f2f,0,1.1,-.2),box(.8,.06,.06,0x222222,0,1.25,-.7),box(.35,.1,.6,0x111111,0,1.02,.5));C.top=42;C.acc=24;C.turn=2.3;C.rad=1;C.cd=6.5}
 else if(type==='lorry'){g=lorryModel(0x3a6bc8);C.top=26;C.acc=9;C.turn=1.25;C.rad=3.3;C.cd=11}
 else{g.add(box(2.4,1,3.6,0xf2b50f,0,1.1,.4),box(1.8,1.3,1.6,0xf2b50f,0,2.25,.8),box(1.84,.8,1.2,0x9ec7e0,0,2.35,.8),box(2.2,.5,.6,0x444444,0,.6,-1.6));
  [[-1.3,1.6],[1.3,1.6],[-1.3,-.9],[1.3,-.9]].forEach(function(p){var t=new THREE.Mesh(new THREE.CylinderGeometry(.8,.8,.5,14),M(0x1a1a1a));t.rotation.z=Math.PI/2;t.position.set(p[0],.8,p[1]);g.add(t)});
  var bm=new THREE.Group(),st=new THREE.Group(),bk=new THREE.Group(),tip=new THREE.Object3D(),soil=box(1.5,.4,.7,0x7a5230,0,-.05,-.5);
  bm.position.set(0,1.7,-1.2);bm.add(box(.35,.35,3.2,0xf2b50f,0,0,-1.6));st.position.set(0,0,-3.2);st.add(box(.3,.3,2.6,0xf2b50f,0,0,-1.3));
  bk.position.set(0,0,-2.6);bk.add(box(1.7,.7,.12,0x444444,0,0,0),box(1.7,.12,.9,0x444444,0,-.3,-.45),box(.1,.55,.9,0x444444,-.8,-.05,-.45),box(.1,.55,.9,0x444444,.8,-.05,-.45),soil);soil.visible=false;
  tip.position.set(0,-.3,-.9);bk.add(tip);st.add(bk);bm.add(st);g.add(bm);bm.rotation.x=.45;st.rotation.x=-.35;bk.rotation.x=.2;
  C.arm={boom:bm,stick:st,bucket:bk,tip:tip,soil:soil};C.top=9;C.acc=6;C.turn=1.3;C.rad=2.6;C.cd=10}
 scene.add(g);return g}
function setVehicle(type,x,z,h,ne){scene.remove(C.g);C.noG=false;C.air=false;C.alt=0;C.fv=0;C.vy=0;C.kind='';C.fc=false;C.hintd=0;C.fuel=100;C.engOff=false;C.fuelOut=false;C.lights=false;C.beam=null;var m=MODELS[type],g;
 if(m){g=car(m.col);g.scale.set(m.sc[0],m.sc[1],m.sc[2]);C.top=m.top;C.acc=m.acc;C.turn=m.turn;C.rad=2.1;C.cd=8}else g=build(type);if(type==='jcb'){jcb.loaded=false;jcb.ph=0;jcb.b=jcb.tb=.45;jcb.k=jcb.tk=.2}
 C.g=g;C.t=type;C.needsFuel=!(C.kind==='heli'||C.kind==='plane'||type==='cycle');C.x=x;C.z=z;C.h=h;C.v=0;g.position.set(x,0,z);g.rotation.y=h;push(C,C.rad);g.position.set(C.x,0,C.z);
 if(!ne){inCar=true;P.x=C.x;P.z=C.z;me.g.visible=(type==='cycle'||type==='bike');spdEl.style.display='block';hint.style.display='none'}}

// weapons
var wm=[],mz=[];
function addW(parts,my){var g=new THREE.Group();parts.forEach(function(p){g.add(p)});var m=new THREE.Object3D();m.position.set(0,my,0);g.add(m);g.position.set(0,-.7,0);g.visible=false;me.aR.add(g);wm.push(g);mz.push(m)}
addW([],0);
addW([box(.04,.35,.1,0xcccccc,0,-.25,0),box(.06,.15,.08,0x222222,0,-.05,0)],-.45);
var bt=new THREE.Mesh(new THREE.CylinderGeometry(.07,.04,1,8),M(0x9a6a33));bt.position.y=-.5;addW([bt],-.9);
addW([box(.07,.3,.1,0x222222,0,-.15,0),box(.06,.14,.08,0x222222,0,-.05,.06)],-.32);
addW([box(.07,.5,.1,0x2a2a2a,0,-.25,0),box(.06,.25,.08,0x222222,0,-.05,.08)],-.55);
addW([box(.08,.9,.1,0x4a5a3a,0,-.4,0),box(.08,.3,.1,0x222222,0,.1,0),box(.05,.12,.06,0x111111,0,-.2,-.09)],-.9);
addW([box(.08,.95,.12,0x2d2a26,0,-.4,0),box(.1,.4,.1,0x6b4423,0,.05,0),box(.05,.2,.08,0x1a1a1a,0,-.55,.12)],-.95);
var rp=new THREE.Mesh(new THREE.CylinderGeometry(.09,.09,1.2,10),M(0x4a5a3a)),wh=new THREE.Mesh(new THREE.ConeGeometry(.14,.3,10),M(0x8a3a2a));rp.position.y=-.3;wh.position.y=-.95;wh.rotation.x=Math.PI;addW([rp,wh],-1.1);
var bb=new THREE.Mesh(new THREE.SphereGeometry(.14,10,8),M(0x222222));bb.position.y=-.1;addW([bb],-.2);
addW([box(.25,.15,.2,0x555555,0,-.08,0),box(.06,.06,.06,0xff2020,0,0,0)],-.2);

// police
var cops=[],pcars=[],tracers=[],rockets=[],expl=[],dv=new THREE.Vector3();
for(var i=0;i<6;i++){var o=human(0x1c3c78,0x16264a,skins[i%5],0x111111);o.g.add(box(.36,.1,.4,0x14284f,0,1.98,-.02));o.g.visible=false;cops.push({o:o,active:false,hp:100,dead:0,ph:0})}
for(var i=0;i<2;i++){var g=car(0x2850a0);g.add(box(1.4,.18,.5,0xffffff,0,1.75,.2),box(.5,.2,.45,0xff2020,-.35,1.92,.2),box(.5,.2,.45,0x2060ff,.35,1.92,.2));g.visible=false;pcars.push({g:g,x:0,z:0,h:0,v:0,active:false,fl:0,l:g.children[g.children.length-2],b:g.children[g.children.length-1]})}
function crime(n){if(n===1){if(wanted<1)wanted=1}else if(n===2)wanted=Math.min(3,wanted+1);else wanted=3;calm=0;ensurePolice()}
function dmgPed(p,d){if(p.dead>0)return;p.hp-=d;if(p.hp<=0){p.dead=4;p.o.g.rotation.x=-1.5;crime(2)}else crime(1)}
function dmgCop(c,d){if(c.dead>0)return;c.hp-=d;if(c.hp<=0){c.dead=5;c.o.g.rotation.x=-1.5;crime(3)}else crime(1)}
function randSpot(a0,a1){for(var i=0;i<25;i++){var a=Math.random()*6.28,r=a0+Math.random()*(a1-a0),x=P.x+Math.cos(a)*r,z=P.z+Math.sin(a)*r;if(Math.abs(x)>HALF||Math.abs(z)>HALF)continue;var bad=false;for(var k=0;k<boxes.length;k++){var b=boxes[k];if(x>b[0]-2&&x<b[1]+2&&z>b[2]-2&&z<b[3]+2){bad=true;break}}if(!bad)return{x:x,z:z}}return null}
function ensurePolice(){var nf=wanted*2,nc=wanted>=2?wanted-1:0;
 cops.forEach(function(c,i){if(i<nf&&!c.active){var s=randSpot(50,80);if(s){c.active=true;c.hp=100;c.dead=0;c.o.g.visible=true;c.o.g.rotation.x=0;c.o.g.position.set(s.x,ground(s.x,s.z),s.z)}}});
 pcars.forEach(function(c,i){if(i<nc&&!c.active){var s=randSpot(70,110);if(s){c.active=true;c.x=s.x;c.z=s.z;c.v=0;c.g.visible=true}}})}
function clearPolice(){cops.forEach(function(c){c.active=false;c.o.g.visible=false});pcars.forEach(function(c){c.active=false;c.g.visible=false})}
function startDown(k){if(down)return;down={k:k,t:4.2,tel:false};bustEl.textContent=k==='busted'?'BUSTED':'WASTED';bustEl.style.opacity=1;firing=false}
function downStep(dt){down.t-=dt;P.vx=P.vz=0;if(inCar)C.v=0;
 if(down.t<2.2&&!down.tel){down.tel=true;inCar=false;me.g.visible=true;me.g.rotation.x=0;spdEl.style.display='none';var f;
  if(down.k==='busted'){f=Math.min(money,150*Math.max(1,wanted));money-=f;P.x=polExit.x;P.z=polExit.z;yaw=face=1.57;hp=Math.max(hp,50);bustEl.textContent='RELEASED FROM POLICE STATION';toast('Fine paid: $'+f)}
  else{f=Math.min(money,100);money-=f;P.x=hosExit.x;P.z=hosExit.z;yaw=face=-1.57;hp=60;bustEl.textContent='TREATED AT HOSPITAL';toast('Hospital bill: $'+f)}
  wanted=0;clearPolice();P.y=.25;P.vy=0}
 if(down.t<=0){bustEl.style.opacity=0;down=null}}
function policeStep(dt){var ps=inCar?Math.abs(C.v):Math.hypot(P.vx,P.vz),close=1e9,caught=false;
 cops.forEach(function(c){if(!c.active)return;var g=c.o.g;if(c.dead>0){c.dead-=dt;if(c.dead<=0){c.active=false;g.visible=false}return}
  var dx=P.x-g.position.x,dz=P.z-g.position.z,d=Math.hypot(dx,dz)||1;close=Math.min(close,d);
  var o={x:g.position.x+dx/d*6.4*dt,z:g.position.z+dz/d*6.4*dt};push(o,.4);g.position.set(o.x,ground(o.x,o.z),o.z);g.rotation.y=Math.atan2(-dx,-dz);c.ph+=dt*11;swing(c.o,c.ph,1);
  if(d<1.6&&ps<11)caught=true});
 pcars.forEach(function(c){if(!c.active)return;var dx=P.x-c.x,dz=P.z-c.z,d=Math.hypot(dx,dz)||1;close=Math.min(close,d);
  c.h+=angd(Math.atan2(-dx,-dz)-c.h)*(1-Math.exp(-3*dt));c.v+=((d<10?3:20)-c.v)*(1-Math.exp(-1.5*dt));
  var o={x:c.x-Math.sin(c.h)*c.v*dt,z:c.z-Math.cos(c.h)*c.v*dt};if(push(o,2.1))c.v*=.5;c.x=o.x;c.z=o.z;c.g.position.set(c.x,0,c.z);c.g.rotation.y=c.h;
  c.fl=(c.fl+dt)%.5;var on=c.fl<.25;c.l.material.color.set(on?0xff2020:0x300000);c.b.material.color.set(on?0x101060:0x2060ff);
  if(d<3.6&&ps<9)caught=true});
 if(close>65)calm+=dt;else calm=0;if(calm>12){wanted=0;clearPolice();toast('Wanted level lost')}
 if(caught)startDown('busted')}

// combat
function tlist(){var a=[];peds.forEach(function(p){if(!(p.dead>0)){var q=p.o.g.position;a.push({x:q.x,y:q.y+1,z:q.z,r:.8,hit:function(d){dmgPed(p,d)}})}});
 cops.forEach(function(c){if(c.active&&!(c.dead>0)){var q=c.o.g.position;a.push({x:q.x,y:q.y+1,z:q.z,r:.8,hit:function(d){dmgCop(c,d)}})}});return a}
function wallDist(o,d,max){for(var t=4;t<max;t+=1){var x=o.x+d.x*t,y=o.y+d.y*t,z=o.z+d.z*t;if(y<.1)return t;for(var i=0;i<boxes.length;i++){var b=boxes[i];if(x>b[0]&&x<b[1]&&z>b[2]&&z<b[3]&&y<b[4])return t}}return max}
function fire(ts){var w=WEAPONS[wi];if(ts-lastFire<w.cd)return;lastFire=ts;
 if(w.melee){atk=.3;var fx=-Math.sin(face),fz=-Math.cos(face);tlist().forEach(function(t){var dx=t.x-P.x,dz=t.z-P.z,d=Math.hypot(dx,dz);if(d<w.melee&&(dx*fx+dz*fz)/Math.max(d,.01)>.3)t.hit(w.dmg)});return}
 cam.getWorldDirection(dv);var o=cam.position,mp=new THREE.Vector3();mz[wi].getWorldPosition(mp);
 if(w.rpg){var rm=new THREE.Mesh(new THREE.CylinderGeometry(.1,.1,.8,8),M(0x555555));scene.add(rm);rockets.push({m:rm,p:mp.clone(),v:dv.clone().multiplyScalar(38),t:4});return}
 var dW=wallDist(o,dv,150),best=null;
 tlist().forEach(function(t){var vx=t.x-o.x,vy=t.y-o.y,vz=t.z-o.z,l=vx*dv.x+vy*dv.y+vz*dv.z;if(l<4.5||l>dW)return;var px=vx-dv.x*l,py=vy-dv.y*l,pz=vz-dv.z*l;if(px*px+py*py+pz*pz<t.r*t.r&&(!best||l<best.l))best={l:l,t:t}});
 var d=best?best.l:dW,end=o.clone().addScaledVector(dv,d),ln=new THREE.Line(new THREE.BufferGeometry().setFromPoints([mp,end]),new THREE.LineBasicMaterial({color:0xffe07a}));scene.add(ln);tracers.push({l:ln,t:.06});
 if(best)best.t.hit(w.dmg);pitch=Math.min(.9,pitch+.008)}
function explode(p){var m=new THREE.Mesh(new THREE.SphereGeometry(1,12,10),new THREE.MeshBasicMaterial({color:0xff9a2e,transparent:true,opacity:.85}));m.position.copy(p);scene.add(m);expl.push({m:m,t:.5});
 tlist().forEach(function(t){var d=Math.hypot(t.x-p.x,t.y-p.y,t.z-p.z);if(d<10)t.hit(160*(1-d/10)+20)});
 var dp=Math.hypot(P.x-p.x,P.y+1-p.y,P.z-p.z);if(dp<6)hurt(35*(1-dp/6)+5)}

// taxi job
var taxi={on:false,stage:0,d0:0},tgt={x:0,z:0},beacon=new THREE.Mesh(new THREE.CylinderGeometry(1.2,1.2,40,12,1,true),new THREE.MeshBasicMaterial({color:0xffd23a,transparent:true,opacity:.45,side:THREE.DoubleSide}));beacon.position.y=20;beacon.visible=false;scene.add(beacon);
function roadPoint(){var r=Math.floor(Math.random()*(N+1)),a=Math.random()<.5,s=(Math.random()-.5)*(HALF*2-40);return a?{x:rc(r),z:s}:{x:s,z:rc(r)}}
function newPickup(){var p=roadPoint();tgt.x=p.x;tgt.z=p.z;taxi.stage=1;beacon.material.color.set(0xffd23a)}
function newDrop(){var p,k=0;do{p=roadPoint()}while(k++<20&&Math.hypot(p.x-C.x,p.z-C.z)<90);tgt.x=p.x;tgt.z=p.z;taxi.stage=2;taxi.d0=Math.hypot(p.x-C.x,p.z-C.z);beacon.material.color.set(0x3adf7a)}
function taxiStep(){if(!taxi.on){beacon.visible=false;return}beacon.visible=true;beacon.position.set(tgt.x,20,tgt.z);
 if(inCar&&isCar(C.t)&&Math.hypot(C.x-tgt.x,C.z-tgt.z)<7&&Math.abs(C.v)<12){
  if(taxi.stage===1){toast('Passenger on board. Drive to the green beacon.');newDrop()}else{var fare=Math.round(15+taxi.d0*.45);money+=fare;toast('Fare delivered: +$'+fare);newPickup()}}}

// phone
var shirtCols=[0xb5483a,0x2f6fb5,0x2f9e5a,0xd0a23a,0x8a4fb0,0x222222,0xeeeeee,0xe0609a];
function setShirt(c){me.g.children[2].material.color.set(c);me.aL.children[0].material.color.set(c);me.aR.children[0].material.color.set(c)}
function drawMap(){var c=document.getElementById('mapc');if(!c)return;var x=c.getContext('2d'),R2=mapR,s=280/(R2*2);function X(v){return (v+R2)*s}
 x.fillStyle='#2f78b5';x.fillRect(0,0,280,280);x.fillStyle='#4b8a46';x.fillRect(X(-350),X(-350),700*s,700*s);ISL.forEach(function(q){x.beginPath();x.arc(X(q.x),X(q.z),(q.r+6)*s,0,7);x.fill()});x.fillStyle='#363b44';for(var r=0;r<=N;r++){x.fillRect(X(rc(r))-ROAD/2*s,0,ROAD*s,280);x.fillRect(0,X(rc(r))-ROAD/2*s,280,ROAD*s)}
 x.font='bold 13px sans-serif';x.textAlign='center';x.textBaseline='middle';
 [[25,25,'H','#e8d9b8','#000'],[-25,25,'+','#fff','#c0392b'],[25,-25,'P','#3b5aa0','#fff'],[-25,-25,'$','#f0702a','#fff']].forEach(function(p){x.fillStyle=p[3];x.beginPath();x.arc(X(p[0]),X(p[1]),9,0,7);x.fill();x.fillStyle=p[4];x.fillText(p[2],X(p[0]),X(p[1])+1)});
 x.fillStyle='#d9892b';[[8.5,-16],[-8.5,16],[8.5,16],[8.5,36]].forEach(function(p){x.fillRect(X(p[0])-3,X(p[1])-3,6,6)});
 if(taxi.on){x.strokeStyle=taxi.stage===1?'#ffd23a':'#3adf7a';x.lineWidth=3;x.beginPath();x.arc(X(tgt.x),X(tgt.z),8,0,7);x.stroke()}
 STOPS.forEach(function(p){if(!p.n)return;x.fillStyle=p.st?'#2f78b5':'#7fb2e5';x.beginPath();x.arc(X(p.x),X(p.z),p.st?8:4,0,7);x.fill();if(p.st){x.fillStyle='#fff';x.fillText('B',X(p.x),X(p.z)+1)}});
 [[-75,-25,'S','#e0a030'],[75,25,'M','#4b9a5a'],[25,75,'C','#c070c0'],[-25,75,'R','#3aa58a'],[125,125,'F','#6b7280'],[175,125,'F','#6b7280'],[125,175,'F','#6b7280'],[-125,125,'F','#6b7280']].forEach(function(p){x.fillStyle=p[3];x.beginPath();x.arc(X(p[0]),X(p[1]),8,0,7);x.fill();x.fillStyle='#fff';x.fillText(p[2],X(p[0]),X(p[1])+1)});
 [[0,385,'Hb'],[310,0,'Ap'],[-290,-250,'Cm'],[25,-75,'Pt'],[-25,-75,'Bk'],[75,-75,'Gn']].forEach(function(p){x.fillStyle='#444a55';x.beginPath();x.arc(X(p[0]),X(p[1]),9,0,7);x.fill();x.fillStyle='#fff';x.font='bold 10px sans-serif';x.fillText(p[2],X(p[0]),X(p[1])+1)});
 ISL.forEach(function(q){x.fillStyle=q.zombie?'#3a5a2a':'#d4af37';x.beginPath();x.arc(X(q.x),X(q.z),9,0,7);x.fill();x.fillStyle='#fff';x.fillText(q.zombie?'Z':'X',X(q.x),X(q.z)+1)});
 buses.forEach(function(b){x.fillStyle='#ffd23a';x.fillRect(X(b.x)-3,X(b.z)-3,6,6)});
 x.fillStyle='#f2c230';x.fillRect(X(C.x)-3,X(C.z)-3,6,6);x.fillStyle='#ff3b4f';x.beginPath();x.arc(X(P.x),X(P.z),5,0,7);x.fill()}
function render(){var h;
 if(cur<0){h='<h3>Home</h3><div class="apps">'+[['Vehicles','🚗'],['Taxi','🚕'],['Bank','💰'],['Map','🗺️'],['Style','👕'],['Parcels','📦'],['Bus','🚌'],['Detonator','💣']].map(function(a,i){return '<button data-a="'+i+'"><b>'+a[1]+'</b>'+a[0]+'</button>'}).join('')+'</div>'}
 else if(cur===0)h='<h3>Order a vehicle</h3><p style="font-size:.8rem">A delivery guy brings it to you. Vehicles you own can be called again for free.</p><div class="vlist">'+ORDER.map(function(t){var o=owned.indexOf(t)>=0;return '<button class="vrow" data-ord="'+t+'"><span>'+vname(t)+'</span><b>'+(o?'Call':'Free')+'</b></button>'}).join('')+'</div>';
 else if(cur===1)h='<h3>Taxi Job</h3><p>'+(taxi.on?(taxi.stage===1?'Drive any car to the yellow beacon to pick up a passenger.':'Take the passenger to the green beacon.'):'Start a shift, then drive any car to the beacons. Fares depend on distance.')+'</p><button class="big" data-act="taxi">'+(taxi.on?'End shift':'Start shift')+'</button>';
 else if(cur===5)h='<h3>Delivery Job</h3><p>Deliver a parcel to a marked location on foot and earn a bonus reward.</p><button class="big" data-act="courier">'+(courier.on?'Cancel delivery':'Start delivery')+'</button>';
 else if(cur===7)h='<h3>Detonator</h3><p>Time bombs planted: '+planted.length+'/3</p><button class="big" data-act="det" style="background:#c0392b">DETONATE</button>';
 else if(cur===6)h='<h3>City Bus</h3><p>Two buses run one loop: Station A, Stand 1, Stand 2, Station B, Stand 3, Stand 4, then back to Station A.</p>'+buses.map(function(b,i){return '<p>Bus '+(i+1)+': '+busLabel(b)+'</p>'}).join('')+'<p>Stand near a stopped bus and press E (or tap Drive) to ride. Press E again at a stop to get off.</p>';
 else if(cur===2)h='<h3>Bank</h3><div class="disp" style="letter-spacing:0;font-size:1.4rem">Cash $'+money+'<br>Bank $'+bank+'</div><p>Deposit and withdraw at the ATMs inside the bank.</p><p>Your vehicles: '+(owned.length?owned.map(vname).join(', '):'none yet')+'</p>';
 else if(cur===3)h='<h3>Map</h3><canvas id="mapc" width="280" height="280" style="width:100%;border-radius:12px"></canvas><p style="font-size:.8rem">H home, + hospital, P police, $ showroom, B bus station, S school, M market, C clothes, R pharmacy, F factory, X treasure, Z zombies, Hb harbour, Ap airport, Cm cemetery, Pt petrol, Bk bank, Gn guns. Tap the map to zoom.</p>';
 else h='<h3>Style</h3><p>Pick your shirt colour</p><div style="text-align:center">'+shirtCols.map(function(c){return '<span class="sw" data-col="'+c+'" style="background:#'+('00000'+c.toString(16)).slice(-6)+'"></span>'}).join('')+'</div>';
 scr.innerHTML=h;if(cur===3)drawMap()}
scr.addEventListener('click',function(e){if(e.target.id==='mapc'){mapR=mapR>300?280:1000;render();return}var b=e.target.closest('button,.sw');if(!b)return;var d=b.dataset;
 if(d.a!==undefined){cur=+d.a;render()}
 else if(d.ord){orderVehicle(d.ord)}
 else if(d.act==='det'){detonate();render()}
 else if(d.act==='taxi'){taxi.on=!taxi.on;if(taxi.on)newPickup();else{beacon.visible=false}render()}
 else if(d.act==='courier'){startCourier();render()}
 else if(d.col){setShirt(+d.col)}});
document.getElementById('phome').addEventListener('click',function(){cur=-1;render()});
document.getElementById('pclose').addEventListener('click',closePhone);
['pointerdown','pointermove','pointerup','pointercancel','mousedown','mouseup'].forEach(function(n){phoneEl.addEventListener(n,function(e){e.stopPropagation()})});
function openPhone(){if(phoneOpen||down||startEl.style.display!=='none')return;phoneOpen=true;keys={};joy=null;look=null;joyEl.style.display='none';firing=false;try{document.exitPointerLock()}catch(e){}phoneEl.style.display='flex';cur=-1;render()}
function closePhone(){phoneOpen=false;phoneEl.style.display='none';if(!touch){try{R.domElement.requestPointerLock()}catch(e){}}}
addEventListener('keydown',function(e){if(!(phoneOpen||down))return;var k=e.key;
 if(phoneOpen){if(k.toLowerCase()==='p'||k==='Escape')closePhone();}
 e.stopImmediatePropagation();e.preventDefault()},true);
function useZone(){if(curZ&&!down&&!phoneOpen)curZ.f()}
addEventListener('keydown',function(e){if(startEl.style.display!=='none'||e.repeat)return;var k=e.key.toLowerCase();if(k==='p')openPhone();else if(k==='f')useZone();else if(k>='0'&&k<='9')selW(k==='0'?9:+k-1);else if(k==='b'&&!inCar)detonate()});
addEventListener('mousedown',function(e){if(startEl.style.display==='none'&&!phoneOpen&&e.button===0)firing=true});addEventListener('mouseup',function(){firing=false});
btn('bf',function(){firing=true},function(){firing=false});btn('bu',useZone);btn('bw',cycleW);btn('bph',openPhone);

// crowd entering through the gate
peds.forEach(function(p){p.hp=100;p.dead=0});
for(var i=0;i<14;i++){var o2=human(shirts[i%7],0x2c3e63,skins[i%5],hairs[i%5]);peds.push({o:o2,ax:0,lat:(i%2?9:-9),s:-HALF-30+i*9,dir:1,ph:i,sp:1.3,hp:100,dead:0})}


// Extra activities: courier deliveries and changing weather
var courier={on:false,target:{x:0,z:0},reward:0},weatherMode=0,rain=[],rainGroup=new THREE.Group();
scene.add(rainGroup);
for(var ri=0;ri<180;ri++){var drop=new THREE.Mesh(new THREE.BoxGeometry(.035,1.1,.035),new THREE.MeshBasicMaterial({color:0xb9d9f5,transparent:true,opacity:.65}));drop.visible=false;rainGroup.add(drop);rain.push(drop)}
function setWeather(){
 weatherMode=(weatherMode+1)%4;
 var names=['Clear','Rain','Storm','Fog'];
 scene.fog.near=weatherMode===3?25:90;scene.fog.far=weatherMode===3?150:380;
 rain.forEach(function(d){d.visible=weatherMode===1||weatherMode===2});
 document.getElementById('weatherBtn').textContent=['🌤️ Clear','🌧️ Rain','⛈️ Storm','🌫️ Fog'][weatherMode];
 toast('Weather: '+names[weatherMode]);
}
function startCourier(){
 if(courier.on){courier.on=false;beacon.visible=false;document.getElementById('jobhud').style.display='none';toast('Delivery job cancelled');return}
 courier.on=true;var q=roadPoint();courier.target=q;courier.reward=80+Math.round(Math.random()*120);
 beacon.position.set(q.x,20,q.z);beacon.material.color.set(0x43c8ff);beacon.visible=true;
 document.getElementById('jobhud').textContent='📦 Deliver the parcel to the blue beacon';
 document.getElementById('jobhud').style.display='block';toast('Delivery started! Follow the blue beacon');
}
function courierStep(){
 if(!courier.on)return;
 beacon.position.set(courier.target.x,20,courier.target.z);
 if(Math.hypot(P.x-courier.target.x,P.z-courier.target.z)<5&&!inCar){
  money+=courier.reward;courier.on=false;beacon.visible=false;
  document.getElementById('jobhud').style.display='none';toast('Parcel delivered! +$'+courier.reward);
 }
}
document.getElementById('weatherBtn').addEventListener('click',setWeather);
document.getElementById('jobBtn').addEventListener('click',startCourier);
addEventListener('keydown',function(e){if(e.repeat||startEl.style.display!=='none'||phoneOpen)return;if(e.key.toLowerCase()==='g')setWeather();if(e.key.toLowerCase()==='j')startCourier()});

// ---- JCB digging
var jcb={b:.45,s:-.35,k:.2,tb:.45,tk:.2,ph:0,t:0,loaded:false,hint:false},tipV=new THREE.Vector3(),jmode=false;
var DIGP=[[.05,-.25,.9],[.1,.95,.8],[.75,.95,.9],[.75,-.9,.8],[.45,.2,.8]];
function startDig(){if(!(inCar&&C.t==='jcb')||jcb.ph)return;jcb.ph=1;jcb.t=0}
addEventListener('keydown',function(e){if(e.key===' '&&!e.repeat&&inCar&&C.t==='jcb'&&!phoneOpen&&!down&&startEl.style.display==='none')startDig()});
btn('jd',startDig);btn('ju',function(){keys.r=1},function(){keys.r=0});btn('jl',function(){keys.v=1},function(){keys.v=0});btn('jk',function(){jcb.tk=jcb.tk>.3?-.8:.95});
function siteLorryStep(dt){
 if(SL.state==='load'){if(SL.load>=6){SL.state='leave';SL.t=0;money+=100;toast('Lorry is full! Bonus +$100');var i=boxes.indexOf(SL.box);if(i>=0)boxes.splice(i,1)}}
 else if(SL.state==='leave'){SL.t+=dt;SL.g.position.x+=Math.min(1,SL.t/1.5)*7*dt;if(SL.t>2.6){SL.state='away';SL.t=0;SL.g.visible=false}}
 else{SL.t+=dt;if(SL.t>10){SL.state='load';SL.load=0;SL.g.position.set(SL.x,0,SL.z);SL.g.visible=true;boxes.push(SL.box)}}
 var s=SL.load/6;SL.soil.visible=SL.load>0;SL.soil.scale.y=Math.max(.01,s*.8);SL.soil.position.y=.08+s*.4}
function jcbStep(dt){var on=inCar&&C.t==='jcb';
 if(on!==jmode){jmode=on;document.body.classList.toggle('jcbmode',on);if(on&&!jcb.hint){jcb.hint=true;toast(touch?'JCB: drive to the soil pile by the house, then tap Dig':'JCB: Space = auto dig. R/V arm, T/B bucket. Dig the soil pile by the house.')}}
 pile=Math.min(40,pile+dt/4);mound.scale.set(3.6,Math.max(.12,pile/40*2.2),3.6);siteLorryStep(dt);
 if(!on||!C.arm)return;var a=C.arm;
 if(jcb.ph){var d=DIGP[jcb.ph-1];jcb.tb=d[0];jcb.tk=d[1];jcb.t+=dt;if(jcb.t>d[2]){jcb.t=0;jcb.ph++;if(jcb.ph>5)jcb.ph=0;if(jcb.ph===3&&!jcb.loaded)toast('Bucket is empty. Drive closer to the soil pile.')}}
 else{if(keys.r)jcb.tb=Math.min(.85,jcb.tb+1.1*dt);if(keys.v)jcb.tb=Math.max(0,jcb.tb-1.1*dt);if(keys.t)jcb.tk=Math.min(1,jcb.tk+2*dt);if(keys.b)jcb.tk=Math.max(-1,jcb.tk-2*dt)}
 var kk=1-Math.exp(-5*dt);jcb.b+=(jcb.tb-jcb.b)*kk;jcb.k+=(jcb.tk-jcb.k)*kk;jcb.s=-.5+(jcb.b+.1)*.25;
 a.boom.rotation.x=jcb.b;a.stick.rotation.x=jcb.s;a.bucket.rotation.x=jcb.k;a.tip.getWorldPosition(tipV);
 if(!jcb.loaded&&jcb.k>.6&&tipV.y<2&&pile>=1&&Math.hypot(tipV.x-PX,tipV.z-PZ)<4.4){jcb.loaded=true;pile-=1;a.soil.visible=true;toast('Soil loaded')}
 else if(jcb.loaded&&jcb.k<-.4&&tipV.y>2){jcb.loaded=false;a.soil.visible=false;var bc=lorryBed();
  if(SL.state==='load'&&Math.hypot(tipV.x-bc.x,tipV.z-bc.z)<3.4){SL.load++;money+=15;toast('Soil in the lorry +$15 ('+SL.load+'/6)')}else toast('Soil spilled. Dump it into the lorry bed.')}}

function ext(dt,now){var ts=now/1000;
 if(toastT>0){toastT-=dt;if(toastT<=0)toastEl.style.opacity=0}
 if(phoneOpen||down){keys={};joy=null}
 if(down)downStep(dt);
 var w=WEAPONS[wi]||WEAPONS[0],ranged=!!(w.rpg||(w.dmg&&!w.melee)),aimNow=ts-lastFire<1.2||firing;
 rain.forEach(function(d){if(d.visible){d.position.set(P.x+(Math.random()-.5)*90,8+Math.random()*22,P.z+(Math.random()-.5)*90);d.rotation.x=.12}});
 courierStep();jcbStep(dt);
 if(firing&&!inCar&&!phoneOpen&&!down)fire(ts);
 wm.forEach(function(g,i){g.visible=(i===wi)&&!inCar});
 if(!inCar&&!down){
  if(ranged){me.aR.rotation.x=aimNow?Math.PI/2+pitch*.9:1;if(ts-lastFire<1.2){face=yaw;me.g.rotation.y=yaw}}
  else if(w.bat){me.aR.rotation.x=atk>0?2.2-3*(1-atk/.3):.7}
  else if(atk>0){me.aR.rotation.x=1.5}}
 if(atk>0)atk-=dt;
 cr2.style.display=(!inCar&&ranged&&!down&&!phoneOpen)?'block':'none';
 for(var i=tracers.length-1;i>=0;i--){tracers[i].t-=dt;if(tracers[i].t<=0){scene.remove(tracers[i].l);tracers[i].l.geometry.dispose();tracers.splice(i,1)}}
 for(var i=rockets.length-1;i>=0;i--){var r=rockets[i];r.p.addScaledVector(r.v,dt);r.m.position.copy(r.p);r.m.quaternion.setFromUnitVectors(new THREE.Vector3(0,1,0),r.v.clone().normalize());r.t-=dt;
  var hit=r.t<=0||r.p.y<.1;if(!hit)for(var k=0;k<boxes.length;k++){var b=boxes[k];if(r.p.x>b[0]&&r.p.x<b[1]&&r.p.z>b[2]&&r.p.z<b[3]&&r.p.y<b[4]){hit=true;break}}
  if(!hit)hit=tlist().some(function(t){return Math.hypot(t.x-r.p.x,t.y-r.p.y,t.z-r.p.z)<1.3});
  if(hit){explode(r.p);scene.remove(r.m);rockets.splice(i,1)}}
 for(var i=expl.length-1;i>=0;i--){var e=expl[i];e.t-=dt;var s=1+(.5-e.t)*18;e.m.scale.setScalar(s);e.m.material.opacity=Math.max(0,e.t*1.6);if(e.t<=0){scene.remove(e.m);expl.splice(i,1)}}
 peds.forEach(function(p){if(p.dead>0){p.dead-=dt;if(p.dead<=0){p.dead=0;p.hp=100;p.o.g.rotation.x=0}}
  else if(inCar&&Math.abs(C.v)>6&&Math.hypot(p.o.g.position.x-C.x,p.o.g.position.z-C.z)<2.2){dmgPed(p,100);C.v*=.85}});
 hurtCool-=dt;if(!inCar&&hurtCool<=0&&!down)traffic.forEach(function(c){if(c.v>3&&P.y<1.5&&Math.hypot(c.g.position.x-P.x,c.g.position.z-P.z)<2){hurt(25);hurtCool=1;toast('Ouch! Watch the traffic')}});
 if(wanted>0&&!down)policeStep(dt);
 taxiStep();
 curZ=null;if(!down&&!phoneOpen&&!riding){var bd=1e9;zones.forEach(function(z){if(!!z.veh!==!!inCar)return;var d=Math.hypot(P.x-z.x,P.z-z.z);if(d<z.r&&d<bd){bd=d;curZ=z}})}
 if(curZ){hint.style.display='block';hint.textContent=(touch?'Tap Use: ':'F: ')+curZ.l()}
 if(inCar&&(C.t==='cycle'||C.t==='bike')&&!down){me.g.visible=true;me.g.position.set(C.x,.2,C.z);me.g.rotation.y=C.h;me.lL.rotation.x=me.lR.rotation.x=-1.2;me.aL.rotation.x=me.aR.rotation.x=-1}
 monEl.textContent='$'+money;hpf.style.width=Math.max(0,hp)+'%';wanEl.textContent=('★').repeat(wanted)+('☆').repeat(5-wanted);
 wpnEl.textContent=inCar?(MODELS[C.t]?MODELS[C.t].n:C.t.toUpperCase()):w.n+' ('+(wi+1)+')';
 if(hp<=0&&!down)startDown('wasted')}

// ---- more vehicles, ordering by phone, aircraft, buses, NPCs
MODELS.mini={n:'Mini City',price:1200,col:0x2fb5a0,sc:[.8,.85,.8],top:27,acc:15,turn:2.2};
MODELS.coupe={n:'Coupe',price:6500,col:0x6a3ab5,sc:[1,.82,1.05],top:44,acc:24,turn:2};
MODELS.roadster={n:'Tesla Roadster',price:14000,col:0xc01818,sc:[1,.74,1.08],top:58,acc:36,turn:2.2};
var VT={cycle:{n:'Bicycle',price:100},bike:{n:'Motorbike',price:900},jcb:{n:'JCB Excavator',price:7000},lorry:{n:'Lorry',price:6000},fcar:{n:'Flying Car',price:20000},heli:{n:'Helicopter',price:30000},plane:{n:'Plane',price:45000}};
var ORDER=['cycle','bike','mini','hatch','sedan','van','pickup','suv','jeep','coupe','sports','electric','roadster','super','jcb','lorry','fcar','heli','plane'];
function vname(t){return MODELS[t]?MODELS[t].n:VT[t].n}
function vprice(t){return MODELS[t]?MODELS[t].price:VT[t].price}
var riding=null,DEL=null,ctl={up:false,dn:false},amode=false;

// aircraft and flying car models
function build(type){
 if(type!=='heli'&&type!=='plane'&&type!=='fcar')return build0(type);
 var g;
 if(type==='heli'){g=new THREE.Group();
  g.add(box(1.9,1.5,3.6,0xd04040,0,1.5,0),box(1.7,1,1.4,0x9ec7e0,0,1.75,-1.6),box(.35,.4,3.4,0xd04040,0,1.9,3.2),box(.1,1.1,.7,0xa03030,0,2.4,4.8),box(.12,.12,3.8,0x333333,-.9,.35,0),box(.12,.12,3.8,0x333333,.9,.35,0),box(.1,.9,.1,0x333333,-.9,.8,-1),box(.1,.9,.1,0x333333,.9,.8,-1),box(.1,.9,.1,0x333333,-.9,.8,1),box(.1,.9,.1,0x333333,.9,.8,1));
  var rot=new THREE.Group();rot.position.set(0,2.45,0);rot.add(box(8,.06,.35,0x222222,0,0,0),box(.35,.06,8,0x222222,0,0,0));g.add(rot,box(.2,.3,.2,0x333333,0,2.3,0));
  var tr=new THREE.Group();tr.position.set(.3,2.3,4.8);tr.add(box(.06,1.2,.2,0x222222,0,0,0));g.add(tr);
  C.rotor=rot;C.trot=tr;C.kind='heli';C.noG=true;C.air=true;C.rad=2.4;C.cd=12;C.top=1;C.acc=0;C.turn=0}
 else if(type==='plane'){g=new THREE.Group();
  g.add(box(1.4,1.3,6.5,0xf0f4f8,0,1.3,0),box(1.2,1.1,1,0x3a6bc8,0,1.3,-3.6),box(11,.15,1.7,0xf0f4f8,0,1.45,-.2),box(1.2,.16,1.72,0x3a6bc8,-5.2,1.45,-.2),box(1.2,.16,1.72,0x3a6bc8,5.2,1.45,-.2),box(.12,1.6,1.1,0x3a6bc8,0,2.2,3),box(3.6,.12,.9,0xf0f4f8,0,1.6,3.1),box(1.2,.6,1.4,0x9ec7e0,0,1.95,-1.3));
  [[-1,-.8],[1,-.8],[0,2.8]].forEach(function(p){var w=new THREE.Mesh(new THREE.CylinderGeometry(.35,.35,.25,10),M(0x1a1a1a));w.rotation.z=Math.PI/2;w.position.set(p[0],.4,p[1]);g.add(w)});
  var pr=new THREE.Group();pr.position.set(0,1.3,-4.2);pr.add(box(.15,2.6,.08,0x222222,0,0,0));g.add(pr);
  C.prop=pr;C.kind='plane';C.noG=true;C.air=true;C.rad=3.2;C.cd=14;C.top=1;C.acc=0;C.turn=0}
 else{g=car(0x7ad0ff);g.scale.set(1,.9,1);var thr=[];
  [[-.95,1.3],[.95,1.3],[-.95,-1.3],[.95,-1.3]].forEach(function(w){var t=new THREE.Mesh(new THREE.CylinderGeometry(.35,.35,.08,10),new THREE.MeshBasicMaterial({color:0x66e0ff}));t.position.set(w[0],.2,w[1]);t.visible=false;g.add(t);thr.push(t)});
  g.add(box(3.2,.06,.7,0x2a3a5a,0,1.4,1.8));C.thr=thr;C.kind='fcar';C.fc=true;C.top=40;C.acc=20;C.turn=2;C.rad=2.1;C.cd=8}
 g.rotation.order='YXZ';scene.add(g);return g}
function pushAir(o,r,y){var hit=false;for(var i=0;i<boxes.length;i++){var b=boxes[i];if(y>b[4]+.8||o.x<b[0]-r||o.x>b[1]+r||o.z<b[2]-r||o.z>b[3]+r)continue;
 var l=o.x-(b[0]-r),rr=(b[1]+r)-o.x,t=o.z-(b[2]-r),bt=(b[3]+r)-o.z,m=Math.min(l,rr,t,bt);if(m===l)o.x=b[0]-r;else if(m===rr)o.x=b[1]+r;else if(m===t)o.z=b[2]-r;else o.z=b[3]+r;hit=true}return hit}
function toggleFly(){if(!(inCar&&C.kind==='fcar'))return;
 if(!C.air){C.air=true;C.noG=true;C.alt=.4;C.vy=3;C.fv=Math.abs(C.v);C.v=0;toast('Flying mode on. Space up, Shift down.')}
 else if(C.alt<3){C.air=false;C.noG=false;C.alt=0;C.v=C.fv*.6;C.vy=0;C.fv=0;toast('Landed')}else toast('Descend to land first')}
function flyStep(dt){var on=inCar&&!!C.kind;
 if(on!==amode){amode=on;document.body.classList.toggle('airmode',on)}
 if(!on)return;
 if(!C.hintd){C.hintd=1;toast(C.kind==='heli'?'Helicopter: W/S fly, A/D turn, Space up, Shift down':C.kind==='plane'?'Plane: W/S throttle, A/D turn, R climb, V dive. Take off from a long road above 100 km/h':'Flying car: press X (or Fly) to take off or land')}
 if(C.kind==='fcar'&&!C.air){C.thr.forEach(function(t){t.visible=false});C.g.rotation.x*=.9;return}
 var ix=(keys.d||keys.arrowright?1:0)-(keys.a||keys.arrowleft?1:0)+(joy?joy.dx:0),iz=(keys.w||keys.arrowup?1:0)-(keys.s||keys.arrowdown?1:0)-(joy?joy.dy:0);
 ix=Math.max(-1,Math.min(1,ix));iz=Math.max(-1,Math.min(1,iz));
 var up=!!(keys[' ']||keys.r||ctl.up),dn=!!(keys.shift||keys.v||ctl.dn),g=C.g;
 if(C.kind==='plane'){
  C.fv+=(iz>0?iz*12:iz*16)*dt;C.fv-=C.fv*(C.alt>.1?.03:.12)*dt;C.fv=Math.max(0,Math.min(75,C.fv));
  var pit=(up?1:0)-(dn?1:0);
  if(C.alt<=.05){C.h-=ix*1.3*dt*Math.min(1,C.fv/10);C.vy=(pit>0&&C.fv>26)?(C.fv-22)*.4:0}
  else{var tg=pit*(C.fv>26?Math.min(14,(C.fv-18)*.5):-4)-(C.fv<26?(26-C.fv)*.5:0);C.vy+=(tg-C.vy)*(1-Math.exp(-2*dt));C.h-=ix*dt*Math.max(.35,Math.min(1.2,C.fv/40))}
  C.alt+=C.vy*dt;if(C.alt<=0){if(C.vy<-9){hurt(30);toast('Hard landing!');C.fv*=.5}C.alt=0;if(C.vy<0)C.vy=0}
  g.rotation.x=Math.max(-.35,Math.min(.35,C.vy*.03))*(C.alt>.1?1:0);g.rotation.z=-ix*.5*(C.alt>.3?1:0);C.prop.rotation.z+=dt*(C.fv>1?50:15)}
 else{
  var tp=C.kind==='fcar'?34:26,tv=iz>0?iz*tp:iz*10;C.fv+=(tv-C.fv)*(1-Math.exp(-1.1*dt));
  var vt=up?(C.kind==='fcar'?10:8):(dn?-8:0);C.vy+=(vt-C.vy)*(1-Math.exp(-3*dt));
  if(C.alt<=.05&&!up){C.vy=Math.max(0,C.vy);C.fv*=.85}
  C.alt=Math.max(0,Math.min(400,C.alt+C.vy*dt));
  if(C.alt>.4)C.h-=ix*(C.kind==='fcar'?1.9:1.5)*dt;
  var a=C.alt>.4?1:0;g.rotation.x=-iz*.16*a;g.rotation.z=-ix*.25*a;
  if(C.rotor){C.rotor.rotation.y+=dt*(C.alt>.05||up?38:10);C.trot.rotation.x+=dt*40}
  if(C.kind==='fcar'){C.thr.forEach(function(t){t.visible=true});if(C.alt<=.05&&C.vy<=0&&!up&&dn)toggleFly()}}
 C.x+=-Math.sin(C.h)*C.fv*dt;C.z+=-Math.cos(C.h)*C.fv*dt;C.x=Math.max(-1300,Math.min(1300,C.x));C.z=Math.max(-1300,Math.min(1300,C.z));
 if(pushAir(C,C.rad,C.alt))C.fv*=.5;
 g.position.set(C.x,C.alt,C.z);g.rotation.y=C.h;spdEl.textContent=Math.round(C.fv*3.6)+' km/h, alt '+Math.round(C.alt)+' m'}
btn('au',function(){ctl.up=true},function(){ctl.up=false});btn('ad',function(){ctl.dn=true},function(){ctl.dn=false});btn('bx',toggleFly);
addEventListener('keydown',function(e){if(e.key.toLowerCase()==='x'&&!e.repeat&&startEl.style.display==='none'&&!phoneOpen&&!down)toggleFly()});

// ordering and delivery
function roadSnap(x,z){var best=null,bd=1e9,cl=function(v){return Math.max(-HALF+20,Math.min(HALF-20,v))};
 for(var r=0;r<=N;r++){var dz=Math.abs(z-rc(r)),dx=Math.abs(x-rc(r));if(dz<bd){bd=dz;best={ax:0,x:cl(x),z:rc(r)}}if(dx<bd){bd=dx;best={ax:1,x:rc(r),z:cl(z)}}}return best}
function orderVehicle(t){if(DEL){toast('A delivery is already on the way');return}
 var has=owned.indexOf(t)>=0;if(!has){if(money<vprice(t)){toast('Not enough money. You need $'+(vprice(t)-money)+' more');return}money-=vprice(t);owned.push(t)}
 startDelivery(t);toast((has?'Calling your ':'Ordered a ')+vname(t)+'. The delivery guy is on the way.');setTimeout(closePhone,700)}
function startDelivery(t){var tx=inCar?C.x:P.x,tz=inCar?C.z:P.z,s=roadSnap(tx,tz),along=s.ax?s.z:s.x,sg=along>0?-1:1;
 if(Math.abs(along+sg*90)>HALF+8)sg=-sg;
 var dx=s.ax?0:-sg,dz=s.ax?-sg:0,sx=s.ax?s.x:s.x+sg*90,sz=s.ax?s.z+sg*90:s.z;
 var truck=lorryModel(0xf5f5f5);truck.add(box(.05,.6,5,0xff7a00,1.21,1.6,1.7),box(.05,.6,5,0xff7a00,-1.21,1.6,1.7));var lb=label('DELIVERY',3.2,.8,'#ff7a00');lb.position.set(0,3.8,-2.5);truck.add(lb);
 truck.position.set(sx,0,sz);truck.rotation.y=Math.atan2(-dx,-dz);
 DEL={t:t,stage:'come',s:s,dx:dx,dz:dz,x:sx,z:sz,v:0,truck:truck,guy:null,tm:0,all:0,ph:0}}
function finishDelivery(force){var D=DEL;if(!D)return;
 if(force&&(D.stage==='come'||D.stage==='walk')){if(!inCar&&!riding)setVehicle(D.t,P.x+4,P.z+4,0,true);else toast('Delivery cancelled')}
 scene.remove(D.truck);if(D.guy)scene.remove(D.guy.g);DEL=null}
function walkGuy(D,tx,tz,dt){var g=D.guy.g,dx=tx-g.position.x,dz=tz-g.position.z,d=Math.hypot(dx,dz)||1,o={x:g.position.x+dx/d*4*dt,z:g.position.z+dz/d*4*dt};
 push(o,.4);g.position.set(o.x,ground(o.x,o.z),o.z);g.rotation.y=Math.atan2(-dx,-dz);D.ph+=dt*10;swing(D.guy,D.ph,1);return d}
function deliveryStep(dt){if(!DEL)return;var D=DEL;D.all+=dt;if(D.all>90){finishDelivery(true);return}
 var tx=inCar?C.x:P.x,tz=inCar?C.z:P.z,h=D.truck.rotation.y;
 if(D.stage==='come'){var rem=(D.s.x-D.x)*D.dx+(D.s.z-D.z)*D.dz,vt=Math.min(16,Math.sqrt(Math.max(0,8*(rem-.5)))+.6);D.v+=(vt-D.v)*(1-Math.exp(-2*dt));D.x+=D.dx*D.v*dt;D.z+=D.dz*D.v*dt;D.truck.position.set(D.x,0,D.z);
  if(rem<1.2&&D.v<1.5){D.stage='walk';D.tm=0;var gy=human(0xff7a00,0x333344,skins[1],0x222222);gy.g.add(box(.36,.1,.4,0xffd23a,0,1.98,-.02));D.guy=gy;gy.g.position.set(D.x+Math.cos(h)*2.6,0,D.z-Math.sin(h)*2.6)}}
 else if(D.stage==='walk'){D.tm+=dt;var gp=D.guy.g.position;
  if(Math.hypot(tx-gp.x,tz-gp.z)>2.2){walkGuy(D,tx,tz,dt);if(D.tm>14)gp.set(tx+1.5,ground(tx,tz),tz)}
  else if(!inCar&&!riding){setVehicle(D.t,D.s.x-D.dx*10,D.s.z-D.dz*10,h,true);toast('Delivery guy: Here is your '+vname(D.t)+'. Enjoy!');D.stage='back';D.tm=0}
  else if(!D.said){D.said=1;toast('Get out of your vehicle to receive the delivery')}}
 else if(D.stage==='back'){D.tm+=dt;var tgx=D.x+Math.cos(h)*2.6,tgz=D.z-Math.sin(h)*2.6;
  if(D.tm<12&&walkGuy(D,tgx,tgz,dt)>.8){}else{scene.remove(D.guy.g);D.guy=null;D.stage='leave';D.tm=0}}
 else{D.v+=(16-D.v)*(1-Math.exp(-1.2*dt));D.x+=D.dx*D.v*dt;D.z+=D.dz*D.v*dt;D.truck.position.set(D.x,0,D.z);D.tm+=dt;if(D.tm>9)finishDelivery(false)}}

// buses
function busModel(){var g=new THREE.Group();g.add(box(2.7,2.4,10.5,0x2a6fd0,0,1.75,0),box(2.74,.9,9.6,0x1d2733,0,2.4,0),box(2.72,.3,10.5,0xffffff,0,1.45,0),box(2.7,.2,10.5,0xeeeeee,0,3,0),box(.05,1.6,1.2,0x9ec7e0,1.38,1.7,-3.6));
 [-3.6,3.6].forEach(function(z){[-1.3,1.3].forEach(function(x){var w=new THREE.Mesh(new THREE.CylinderGeometry(.55,.55,.4,14),M(0x1a1a1a));w.rotation.z=Math.PI/2;w.position.set(x,.55,z);g.add(w)})});
 var lb=label('CITY BUS',4,1,'#1d2733');lb.position.set(0,4,-5.4);g.add(lb);scene.add(g);return g}
var buses=[0,5].map(function(si,k){var p=STOPS[si],q=STOPS[(si+1)%STOPS.length],b={g:busModel(),x:p.x,z:p.z,h:Math.atan2(-(q.x-p.x),-(q.z-p.z)),v:0,wi:si,wait:6+k*3};b.g.position.set(b.x,0,b.z);b.g.rotation.y=b.h;return b});
function busLabel(b){var L=STOPS.length,i=b.wi,k=0;if(b.wait>0&&STOPS[i].n)return 'At '+STOPS[i].n;while(k++<L&&!STOPS[i].n)i=(i+1)%L;return 'Next: '+STOPS[i].n}
function nearBus(){var r=null;buses.forEach(function(b){if((b.wait>0||b.v<.4)&&Math.hypot(b.x-P.x,b.z-P.z)<8)r=b});return r}
function boardBus(b){riding=b;me.g.visible=false;firing=false;toast('You boarded the bus. '+busLabel(b))}
function leaveBus(){var b=riding;if(!(b.wait>0||b.v<.4)){toast('Wait until the bus stops');return}riding=null;me.g.visible=true;var wpx=(b.route||STOPS)[b.wi];if(wpx&&wpx.ex!==undefined){P.x=wpx.ex;P.z=wpx.ez}else{P.x=b.x+Math.cos(b.h)*4;P.z=b.z-Math.sin(b.h)*4}P.y=ground(P.x,P.z);P.vx=P.vz=0}
waiting.forEach(function(w){w.t=0;w.npcs=w.pts.map(function(p,i){var o=human(shirts[(i+w.i)%7],0x2c3e63,skins[(i+w.i)%5],hairs[(i*2+w.i)%5]);o.g.position.set(p[0],ground(p[0],p[1]),p[1]);o.g.rotation.y=Math.PI/2*(p[0]<0?-1:1);return o})});
function busStep(dt){
 buses.forEach(function(b){var R_=b.route||STOPS,L=R_.length;
  if(b.wait>0){b.wait-=dt;b.v=0;if(b.wait<=0)b.wi=(b.wi+1)%L}
  else{var wp=R_[b.wi],dx=wp.x-b.x,dz=wp.z-b.z,d=Math.hypot(dx,dz);
   if(d<.7){b.v=0;if(wp.stop){b.wait=wp.stop;if(riding===b)toast('Arrived at '+wp.n+'. Press E to get off.')}else b.wi=(b.wi+1)%L}
   else{var vmax=wp.stop?Math.min(11,Math.sqrt(Math.max(0,24*(d-.5)))+.5):(d<16?6:11),tg=riding===b?null:(inCar?C:P);
    if(tg){var rx=tg.x-b.x,rz=tg.z-b.z,fx=dx/d,fz=dz/d,ah=rx*fx+rz*fz,lat=Math.abs(rx*fz-rz*fx);if(ah>0&&ah<13&&lat<3.2)vmax=0}
    b.v+=(vmax-b.v)*(1-Math.exp(-2*dt));var st=Math.min(d,b.v*dt);b.x+=dx/d*st;b.z+=dz/d*st;b.h+=angd(Math.atan2(-dx,-dz)-b.h)*(1-Math.exp(-4*dt))}}
  b.g.position.set(b.x,0,b.z);b.g.rotation.y=b.h});
 waiting.forEach(function(w){var here=buses.some(function(b){return b.wait>0&&Math.hypot(b.x-w.x,b.z-w.z)<8});
  if(here){w.t=6;w.npcs.forEach(function(o){o.g.visible=false})}else if(w.t>0){w.t-=dt;if(w.t<=0)w.npcs.forEach(function(o){o.g.visible=true})}});
 kids.forEach(function(k){var g=k.o.g,dx=k.tx-g.position.x,dz=k.tz-g.position.z,d=Math.hypot(dx,dz);
  if(d<.6){k.tx=YARD.x0+Math.random()*(YARD.x1-YARD.x0);k.tz=YARD.z0+Math.random()*(YARD.z1-YARD.z0)}
  else{g.position.x+=dx/d*1.5*dt;g.position.z+=dz/d*1.5*dt;g.position.y=.25;g.rotation.y=Math.atan2(-dx,-dz);k.ph+=dt*8;swing(k.o,k.ph,.9)}});
 smoke.forEach(function(s){s.t+=dt;var k=(s.t%4)/4;s.m.position.set(s.x+k*3,s.y+k*10,s.z);s.m.scale.setScalar(1+k*2.5);s.m.material.opacity=.5*(1-k)});
 if(riding){firing=false;P.x=riding.x;P.z=riding.z;P.y=1.2;P.vx=P.vz=0;me.g.visible=false;wpnEl.textContent='Bus: '+busLabel(riding)}
 else if(!inCar&&!down&&!phoneOpen&&nearBus()){hint.style.display='block';hint.textContent=touch?'Tap Drive to board the bus':'Press E to board the bus'}}

// more NPCs: pedestrians around town and children in the school yard
for(var i=0;i<40;i++){var o3=human(shirts[(i+2)%7],[0x2c3e63,0x4a4a4a,0x6b5a3a][i%3],skins[(i+1)%5],hairs[(i*2)%5]);
 peds.push({o:o3,ax:i%2,lat:rc(Math.floor(hash(i,7,40)*(N+1)))+(hash(i,8,40)<.5?-9:9),s:(hash(i,9,40)-.5)*HALF*2,dir:hash(i,10,40)<.5?-1:1,ph:hash(i,11,40)*6,sp:1+hash(i,12,40)*.6,hp:100,dead:0})}
if(YARD.x1>YARD.x0)for(var i=0;i<12;i++){var o4=human(shirts[i%7],0x3a4a8a,skins[i%5],hairs[i%5]);o4.g.scale.setScalar(.72);var kx=YARD.x0+Math.random()*(YARD.x1-YARD.x0),kz=YARD.z0+Math.random()*(YARD.z1-YARD.z0);o4.g.position.set(kx,.25,kz);kids.push({o:o4,tx:kx,tz:kz,ph:0})}

// ---- B4: player look, weapons, police 1-5 stars, fuel, switches, zombies, ghosts, sharks, ferry
var chaseT=0,swimT=0,planted=[],gren=[],ghostCool=0,zCool=0,sharkCool=0,cmode=false;
(function(){me.g.add(box(.64,.85,.38,0xf8f3e6,0,.5,0),box(.66,.07,.4,0xd4af37,0,.1,0),box(.58,.1,.34,0xd4af37,0,.93,0));
 [[0,0],[.09,0],[-.09,0],[0,.09],[0,-.09],[.065,.065],[-.065,-.065],[.065,-.065],[-.065,.065]].forEach(function(p){var c=new THREE.Mesh(new THREE.ConeGeometry(.045,.2,6),M(0x050505));c.position.set(p[0],2.03,p[1]);c.rotation.z=-p[0]*4;c.rotation.x=p[1]*4;me.g.add(c)})})();

// weapons
function selW(i){if(!wown[i]){toast('Get it from the gun shop first');return}wi=i}
function cycleW(){for(var k=1;k<=10;k++){var j=(wi+k)%10;if(wown[j]){wi=j;return}}}
function plantBomb(x,z){var g=new THREE.Group();g.add(box(.5,.25,.35,0x444444,0,.12,0));var l=new THREE.Mesh(new THREE.SphereGeometry(.06,6,5),new THREE.MeshBasicMaterial({color:0xff2020}));l.position.set(0,.3,0);g.add(l);g.position.set(x,ground(x,z),z);scene.add(g);planted.push({g:g,l:l,x:x,z:z});toast('Time bomb planted ('+planted.length+'/3). Detonate with B or the phone Detonator app')}
function detonate(){if(!planted.length){toast('No time bombs planted');return}planted.forEach(function(b){explode(new THREE.Vector3(b.x,.6,b.z));scene.remove(b.g)});planted=[]}
function fire(ts){var w=WEAPONS[wi];if(!wown[wi]||ts-lastFire<w.cd)return;lastFire=ts;
 if(w.melee){atk=.3;var fx=-Math.sin(face),fz=-Math.cos(face);tlist().forEach(function(t){var dx=t.x-P.x,dz=t.z-P.z,d=Math.hypot(dx,dz);if(d<w.melee&&(dx*fx+dz*fz)/Math.max(d,.01)>.3)t.hit(w.dmg)});return}
 cam.getWorldDirection(dv);var o=cam.position,mp=new THREE.Vector3();mz[wi].getWorldPosition(mp);
 if(w.rpg){var rm=new THREE.Mesh(new THREE.CylinderGeometry(.1,.1,.8,8),M(0x555555));scene.add(rm);rockets.push({m:rm,p:mp.clone(),v:dv.clone().multiplyScalar(38),t:4});return}
 if(w.bomb){var bm=new THREE.Mesh(new THREE.SphereGeometry(.18,10,8),M(0x222222));scene.add(bm);gren.push({m:bm,p:mp.clone(),v:dv.clone().multiplyScalar(15).add(new THREE.Vector3(0,4,0)),t:2.2});atk=.3;return}
 if(w.tbomb){if(planted.length>=3){toast('Max 3 time bombs. Detonate first (B or phone)');return}plantBomb(P.x-Math.sin(face)*1.2,P.z-Math.cos(face)*1.2);atk=.3;return}
 var dW=wallDist(o,dv,150),best=null;
 tlist().forEach(function(t){var vx=t.x-o.x,vy=t.y-o.y,vz=t.z-o.z,l=vx*dv.x+vy*dv.y+vz*dv.z;if(l<4.5||l>dW)return;var px=vx-dv.x*l,py=vy-dv.y*l,pz=vz-dv.z*l;if(px*px+py*py+pz*pz<t.r*t.r&&(!best||l<best.l))best={l:l,t:t}});
 var d=best?best.l:dW,end=o.clone().addScaledVector(dv,d),ln=new THREE.Line(new THREE.BufferGeometry().setFromPoints([mp,end]),new THREE.LineBasicMaterial({color:0xffe07a}));scene.add(ln);tracers.push({l:ln,t:.06});
 if(best)best.t.hit(w.dmg);pitch=Math.min(.9,pitch+.008)}
function weaponStep(dt){
 for(var i=gren.length-1;i>=0;i--){var g=gren[i];g.v.y-=18*dt;g.p.addScaledVector(g.v,dt);if(g.p.y<.2){g.p.y=.2;g.v.y=0;g.v.x*=.6;g.v.z*=.6}g.m.position.copy(g.p);g.t-=dt;if(g.t<=0){explode(g.p);scene.remove(g.m);gren.splice(i,1)}}
 planted.forEach(function(b){b.l.visible=(Math.floor(performance.now()/400)%2)===0})}

// police: 1 foot, 2 + bikes, 3 + cars, 4 + helicopter, 5 + tank. Each chase lasts 10 seconds.
var bikesP=[],heliP,tankP;
(function(){var g=car(0x2850a0);g.add(box(1.4,.18,.5,0xffffff,0,1.75,.2),box(.5,.2,.45,0xff2020,-.35,1.92,.2),box(.5,.2,.45,0x2060ff,.35,1.92,.2));g.visible=false;pcars.push({g:g,x:0,z:0,h:0,v:0,active:false,fl:0,l:g.children[g.children.length-2],b:g.children[g.children.length-1]})})();
for(var i=0;i<4;i++){var bg=new THREE.Group();[-.8,.8].forEach(function(z){var w=wheel(.4,.1);w.position.set(0,.42,z);bg.add(w)});bg.add(box(.4,.5,1.4,0x2850a0,0,.8,0),box(.35,.3,.6,0xffffff,0,1.1,-.2),box(.8,.06,.06,0x222222,0,1.25,-.7),box(.3,.12,.3,0xff2020,0,1.4,.5));bg.visible=false;scene.add(bg);bikesP.push({g:bg,x:0,z:0,h:0,v:0,active:false})}
(function(){var g=new THREE.Group();g.add(box(1.9,1.5,3.6,0x2850a0,0,1.5,0),box(1.7,1,1.4,0x9ec7e0,0,1.75,-1.6),box(.35,.4,3.4,0xffffff,0,1.9,3.2),box(.1,1.1,.7,0xffffff,0,2.4,4.8),box(.12,.12,3.8,0x333333,-.9,.35,0),box(.12,.12,3.8,0x333333,.9,.35,0),box(.4,.2,.4,0xff2020,0,2.7,0));
 var rot=new THREE.Group();rot.position.set(0,2.45,0);rot.add(box(8,.06,.35,0x222222,0,0,0),box(.35,.06,8,0x222222,0,0,0));g.add(rot);g.visible=false;scene.add(g);heliP={g:g,rot:rot,x:0,z:0,h:0,alt:16,active:false}})();
(function(){var g=new THREE.Group();g.add(box(3.4,1,6.4,0x4a5a3a,0,1,0),box(.7,.9,6.6,0x222222,-1.5,.5,0),box(.7,.9,6.6,0x222222,1.5,.5,0),box(2,.9,2.4,0x56683f,0,1.9,.3),box(.3,.3,3.6,0x2a2a2a,0,2,-2.4),box(.5,.15,.5,0xff2020,0,2.5,.9));g.visible=false;scene.add(g);tankP={g:g,x:0,z:0,h:0,v:0,active:false}})();
function setStars(k){wanted=Math.max(wanted,Math.min(5,k));chaseT=10;ensurePolice()}
function crime(n){if(n===1){if(wanted<1)wanted=1}else if(n===2)wanted=Math.min(5,wanted+1);else wanted=Math.min(5,wanted+2);chaseT=10;calm=0;ensurePolice()}
function placeU(u,a0,a1){var s=randSpot(a0,a1);if(!s)return;u.active=true;u.x=s.x;u.z=s.z;u.v=0;u.g.visible=true;u.g.position.set(s.x,0,s.z)}
function ensurePolice(){var w=wanted,nf=w>=5?3:2,nb=w<2?0:(w>=4?3:2),nc=w<3?0:(w>=5?3:2);
 cops.forEach(function(c,i){if(i<nf&&!c.active){var s=randSpot(50,80);if(s){c.active=true;c.hp=100;c.dead=0;c.o.g.visible=true;c.o.g.rotation.x=0;c.o.g.position.set(s.x,ground(s.x,s.z),s.z)}}});
 bikesP.forEach(function(b,i){if(i<nb&&!b.active)placeU(b,60,90)});pcars.forEach(function(c,i){if(i<nc&&!c.active)placeU(c,70,110)});
 if(w>=4&&!heliP.active){placeU(heliP,70,100);heliP.alt=18}if(w>=5&&!tankP.active)placeU(tankP,70,100)}
function clearPolice(){cops.forEach(function(c){c.active=false;c.o.g.visible=false});pcars.concat(bikesP).forEach(function(c){c.active=false;c.g.visible=false});heliP.active=false;heliP.g.visible=false;tankP.active=false;tankP.g.visible=false}
function policeStep(dt){var air=inCar&&(C.alt||0)>3,ps=inCar?Math.abs(C.noG?C.fv:C.v):Math.hypot(P.vx,P.vz),caught=false;
 chaseT-=dt;if(chaseT<=0){wanted=0;clearPolice();toast('The police gave up the chase');return}
 cops.forEach(function(c){if(!c.active)return;var g=c.o.g;if(c.dead>0){c.dead-=dt;if(c.dead<=0){c.active=false;g.visible=false}return}
  var dx=P.x-g.position.x,dz=P.z-g.position.z,d=Math.hypot(dx,dz)||1,o={x:g.position.x+dx/d*6.4*dt,z:g.position.z+dz/d*6.4*dt};push(o,.4);g.position.set(o.x,ground(o.x,o.z),o.z);g.rotation.y=Math.atan2(-dx,-dz);c.ph+=dt*11;swing(c.o,c.ph,1);
  if(d<1.6&&ps<11&&!air)caught=true});
 function drive(c,sp,rad,arr,ar){if(!c.active)return;var dx=P.x-c.x,dz=P.z-c.z,d=Math.hypot(dx,dz)||1;c.h+=angd(Math.atan2(-dx,-dz)-c.h)*(1-Math.exp(-3*dt));c.v+=((d<10?3:sp)-c.v)*(1-Math.exp(-1.5*dt));
  var o={x:c.x-Math.sin(c.h)*c.v*dt,z:c.z-Math.cos(c.h)*c.v*dt};if(push(o,rad))c.v*=.5;c.x=o.x;c.z=o.z;c.g.position.set(c.x,0,c.z);c.g.rotation.y=c.h;
  if(c.l){c.fl=(c.fl+dt)%.5;var on=c.fl<.25;c.l.material.color.set(on?0xff2020:0x300000);c.b.material.color.set(on?0x101060:0x2060ff)}
  if(d<ar&&ps<arr&&!air)caught=true}
 pcars.forEach(function(c){drive(c,20,2.1,9,3.6)});bikesP.forEach(function(c){drive(c,21,1.2,12,2.6)});drive(tankP,9,2.8,10,5);
 if(heliP.active){var h=heliP,dx=P.x-h.x,dz=P.z-h.z,d=Math.hypot(dx,dz)||1,sp=d>8?24:Math.min(24,d*3);h.x+=dx/d*sp*dt;h.z+=dz/d*sp*dt;h.alt+=((d<14?9:18)-h.alt)*(1-Math.exp(-1.5*dt));h.h=Math.atan2(-dx,-dz);
  h.g.position.set(h.x,h.alt,h.z);h.g.rotation.y=h.h;h.rot.rotation.y+=dt*38;if(d<6&&ps<8&&!air)caught=true}
 if(caught)startDown('busted')}

// fuel, switches, drive pad
function toggleEngine(){if(!inCar||!C.needsFuel)return;C.engOff=!C.engOff;toast('Engine '+(C.engOff?'off':'on'))}
function toggleLights(){if(!inCar||C.kind==='heli'||C.kind==='plane')return;C.lights=!C.lights;if(C.beam){C.g.remove(C.beam);C.beam=null}
 if(C.lights){var b=new THREE.Group();[-.6,.6].forEach(function(x){var c=new THREE.Mesh(new THREE.ConeGeometry(1.2,6,10,1,true),new THREE.MeshBasicMaterial({color:0xfff3b0,transparent:true,opacity:.22,side:THREE.DoubleSide}));c.rotation.x=Math.PI/2;c.position.set(x,.8,-3.5);b.add(c)});C.g.add(b);C.beam=b}toast('Lights '+(C.lights?'on':'off'))}
btn('cg',function(){keys.w=1},function(){keys.w=0});btn('ck',function(){keys.s=1},function(){keys.s=0});btn('cl',function(){keys.a=1},function(){keys.a=0});btn('cr',function(){keys.d=1},function(){keys.d=0});btn('ce',toggleEngine);btn('cn',toggleLights);
addEventListener('keydown',function(e){if(e.repeat||startEl.style.display!=='none'||phoneOpen||down)return;var k=e.key.toLowerCase();if(k==='i')toggleEngine();else if(k==='l')toggleLights()});
function fuelStep(dt){var cm=inCar&&!C.kind&&C.t!=='jcb'&&!riding;if(cm!==cmode){cmode=cm;document.body.classList.toggle('carmode',cm)}
 if(!inCar||!C.needsFuel){C.fuelOut=false;return}
 var sp=Math.abs(C.noG?C.fv:C.v);if(!C.engOff&&sp>.2)C.fuel=Math.max(0,C.fuel-(.08+sp*.012)*dt);
 C.fuelOut=C.fuel<=0;if(C.fuelOut&&!C.fw){C.fw=1;toast('Out of petrol! Find a petrol pump')}if(!C.fuelOut)C.fw=0;
 if(C.fuelOut&&C.kind==='fcar'&&C.air){C.alt=Math.max(0,C.alt-6*dt);C.fv*=.98;if(C.alt<=.05){C.air=false;C.noG=false;C.alt=0;C.v=0;C.fv=0}}
 spdEl.textContent+='  fuel '+Math.round(C.fuel)+'%'+(C.engOff?' (engine off)':'')}

// zombies, ghosts, sharks, ferry, bank doors, swimming
var Zs=[],Gh=[],Sk=[];
(function(){var s=ISL[3];for(var i=0;i<14;i++){var o=human(0x3a2f2a,0x2a2a35,0x7ea86a,0x1a1a1a),a=hash(i,1,60)*6.28,r=Math.sqrt(hash(i,2,60))*(s.r-25),x=s.x+Math.cos(a)*r,z=s.z+Math.sin(a)*r;o.g.position.set(x,0,z);Zs.push({o:o,hp:100,dead:0,hx:x,hz:z,ph:i,wa:a})}
 for(var i=0;i<8;i++){var g=new THREE.Group(),m=new THREE.MeshBasicMaterial({color:0xe8f4ff,transparent:true,opacity:.55});var bd=new THREE.Mesh(new THREE.ConeGeometry(.7,2.2,10),m);bd.position.y=1.1;var hd=new THREE.Mesh(new THREE.SphereGeometry(.4,10,8),m);hd.position.y=2.4;g.add(bd,hd,box(.1,.14,.05,0x111111,-.14,2.45,-.36),box(.1,.14,.05,0x111111,.14,2.45,-.36));
  var x=-290+(hash(i,5,61)-.5)*50,z=-250+(hash(i,6,61)-.5)*50;g.position.set(x,0,z);scene.add(g);Gh.push({g:g,m:m,hp:50,dead:0,ph:i,wa:hash(i,7,61)*6.28})}
 for(var i=0;i<3;i++){var g2=new THREE.Group();g2.add(box(.9,.5,3.2,0x6b7d8c,0,0,0),box(.2,.8,.9,0x56677a,0,.5,.2),box(.15,.7,.7,0x56677a,0,.1,1.8));g2.position.set(-60,-.15,425);scene.add(g2);Sk.push({g:g2,a:i*2.1,r:16+i*5})}})();
function dmgZ(z,d){if(z.dead>0)return;z.hp-=d;if(z.hp<=0){z.dead=25;z.o.g.rotation.x=-1.5;money+=100;toast('Zombie killed! +$100')}}
function tlist(){var a=[];peds.forEach(function(p){if(!(p.dead>0)){var q=p.o.g.position;a.push({x:q.x,y:q.y+1,z:q.z,r:.8,hit:function(d){dmgPed(p,d)}})}});
 cops.forEach(function(c){if(c.active&&!(c.dead>0)){var q=c.o.g.position;a.push({x:q.x,y:q.y+1,z:q.z,r:.8,hit:function(d){dmgCop(c,d)}})}});
 Zs.forEach(function(z){if(!(z.dead>0)){var q=z.o.g.position;a.push({x:q.x,y:q.y+1,z:q.z,r:.8,hit:function(d){dmgZ(z,d)}})}});
 Gh.forEach(function(g){if(!(g.dead>0)){var q=g.g.position;a.push({x:q.x,y:q.y+1.3,z:q.z,r:1,hit:function(d){g.hp-=d;if(g.hp<=0){g.dead=25;g.g.visible=false}}})}});return a}
var FRK=[];(function(){FRK=[{x:9.5,z:400,stop:12,n:'Harbour',ex:5,ez:400},{x:-120,z:470}];[0,1,2].forEach(function(i){var s=ISL[i];FRK.push({x:s.x,z:s.z-s.r-20,stop:12,n:'Treasure Island '+(i+1),ex:s.x,ez:s.z-s.r-11});if(i===0)FRK.push({x:-200,z:615});if(i===1)FRK.push({x:-20,z:745})});
 FRK.push({x:330,z:560});var z=ISL[3];FRK.push({x:z.x,z:z.z-z.r-20,stop:12,n:'Zombie Island',ex:z.x,ez:z.z-z.r-11},{x:200,z:470});
 var g=new THREE.Group();g.add(box(6,1.6,16,0xf4f4f4,0,.2,0),box(4,2.2,6,0x2a6fd0,0,2,2),box(1.2,2,1.2,0xc0392b,0,3.8,3));var lb=label('FERRY',4,1,'#2a6fd0');lb.position.set(0,5.5,0);g.add(lb);scene.add(g);
 var b={g:g,route:FRK,x:9.5,z:400,h:Math.atan2(-(FRK[1].x-9.5),-(FRK[1].z-400)),v:0,wi:0,wait:8,ferry:1};g.position.set(b.x,0,b.z);g.rotation.y=b.h;buses.push(b)})();
function busLabel(b){var R_=b.route||STOPS,L=R_.length,i=b.wi,k=0;if(b.wait>0&&R_[i].n)return 'At '+R_[i].n;while(k++<L&&!R_[i].n)i=(i+1)%L;return 'Next: '+R_[i].n}
function nearTraffic(){var r=null,bd=4.5;tr
