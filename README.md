variáveis da bolinha
deixe xbolinha = 300;
deixe a ybolinha = 200;
diâmetro de saída = 13;
deixe raio = diametro / 2 ;

velocidade da bolinha 
deixe velocidadeXbolinha = 6;
deixe velocidadeYbolinha = 6;
deixe raqueteComprimento = 10;
deixe raqueteAltura = 90;

variáveis da raquete
deixe xraquete = 5;
deixe yraquete = 150;

variáveis do oponente
deixe xRaqueteOponente = 585;
deixe yRaqueteOponente = 150;
vamos lá;

let colidiu = falso;

placar do jogo |
deixe meusPontos = 0;
deixe pontosDoOponente = 0;

sons do jogo |
deixe a raquetada;
deixe ponto;
deixe trilha;

função preload(){
  trilha = loadSound("trilha.mp3");
  ponnto = loadSound("ponto.mp3");
  raquetada = loadSound("raquetada.mp3");
}

função setup() {
  createCanvas(600, 400);
  trilha.loop();
}

função draw() {
 antecedentes (0); 
 mostra Bolinha();
  movimentaBolinha();
  verificaColisaoBorda();
 mostra Raquete(xraquete, yraquete);
  movimentaMinhaRaquete();
 verificaColisaoRaquete();
  verificaColisaoRaquete(xRaquete, yRaquete);
  mostraRaquete(xraqueteOponente, yRaqueteOponente);
  movimentaRaqueteOponente();
  verificaColisaoRaquete(xRaqueteOponente, yRaqueteOponente);
  incluiPlacar() ;
  marcaPonto();
}

função mostraBolinha(){
 círculo(xbolinha, ybolinha, diametro);
}

 função movimentaBolinha(){
 xbolinha += velocidadeXbolinha;
  ybolinha += velocidadeYbolinha;
}

function verificaColisaoBorda(){
 se (xbolinha + raio> largura ||
 XBOLINHA - Raio< 0){
  velocidadeXbolinha *= -1;
 } 
 se (ybolinha + raio> altura || 
    ybolinha - raio < 0){
   velocidadeYbolinha *= -1;
    }   
}

função mostraRaquetex(x,y) {
  rect(x, y, raqueteComprimento, 
       raqueteAltura);
}

função movimentaMinhaRaquete() {
  if(keyIsDown(UP_ARROW)){
    yraquete -= 10;
  }
  if(keyIsDown(DOWN_ARROW)) {
    yraquete +=10;
  }
}

function verificaColisaoRaquete(){
if (xbolinha - raio < xRaquete + raqueteComprimento && yBolinha - raio < yRaquete + raquetealtura && yBolinha + raio > yRaquete){
    velocidadeXbolinha *= -1;
 Raquetada.Play();
  }
}

function verifacaColisaoRaquete(x, y){
  colidiu = collideReactCircle(x, y, raqueteComprimento,raqueteAltura,xBolinha,yBolinha,raio);
 se (colidiu){
    velocidadeXBolinha *= -1;
 Raquetada.Play();
  }
}

function movimentaRaqueteOponente(){
  velocidadeYOponente = yBolinha -yRaqueteOponente -raqueteComprimento / 2 - 30;
  yRaqueteOponente += velocidadeYoponente
}

function incluiplacar(){
 acidente vascular cerebral (255);
 textAlign(CENTRO);
 tamanho do texto(16);
 preenchimento (cor (255, 140, 0));
 ret(150, 10, 40, 20);
 preenchimento (255);
 texto (Meuspontos, 170, 26);
 preenchimento(cor(255, 140, 0));
 reagir(450, 10, 40, 20);
 preenchimento (255);
 texto (pontoDoOponente, 470, 26);
}

função marcaPonto(){
  if (xBolinha > 590){
    meusPontos += 1;
    ponto.play();
  }
if (xbolinha < 10){
  pontosDoOponente += 1;
  ponto.play();
