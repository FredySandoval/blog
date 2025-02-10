<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
 <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.7.3/p5.min.js"></script>
# hello world what up


<iframe src="https://editor.p5js.org/shockerovip/full/5kVSPiuEX"></iframe>


**The Cauchy-Schwarz Inequality**\
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

<script >
  let total = 3;let angle =0;let r;
let b = 0.03; let c = 0;
function setup() {
  createCanvas(windowWidth,windowHeight);
   r = height/2.5;
}

function draw() {
  background(0);
  translate(width/2,height/2);
  rotate(PI/3.2)
  stroke(255);strokeWeight(1);
  let path = [];noFill();
  star(0,0,10,30,5);

  for(let i =0;i<total;i++){
  	let num = 360/total;
    let x = cos(angle + num * i * PI/180) * r;
    let y = sin(angle + num * i * PI/180) * r;
    // point(x,y);
    //strokeWeight(1);
    star(x,y,20,50,i+5%15);
    let v = createVector(x,y)
    path[i] = v;
// }

 for(let j = 0 ;j< path.length -1; j++){
   for(let i = 0 ;i< path.length-1 ; i++){
     let t = i ;
     strokeWeight(0.4);
     
     stroke('rgb(100%,100%,100%)');
      rotat(path[j].x,path[j].y, path[i+1].x,path[i+1].y,c);
   }
 }
} 
  if(total <=13){
  total=total + b; 
     }
  c+=0.04;

}


function star(x, y, radius1, radius2, npoints) {
  strokeWeight(1);
  stroke('rgb(100%,100%,0%)');
 
  let angle = TWO_PI / npoints;
  let halfAngle = angle / 2.0;
  beginShape();
  for (let a = 0; a < TWO_PI; a += angle) {
    let sx = x + cos(a) * radius2;
    let sy = y + sin(a) * radius2;
    vertex(sx, sy);
    sx = x + cos(a + halfAngle) * radius1;
    sy = y + sin(a + halfAngle) * radius1;
    vertex(sx, sy);
  }
  endShape(CLOSE);
}
function rotat(x1,y1, x2,y2, angle) {//angle in radians
    let a = [];
    let b = [];
    let angle_degrees = angle;
    // angle_radians = angle_degrees*PI/180; //to turn to degrees
    a[0]= x1;
    a[1]= y1;
    b[0]= x2;
    b[1]= y2;                       
    // a and b are arrays of length 2 with the x, y coordinate of
    // your segments extreme points with the form [x, y]

    midpoint = [
        (a[0] + b[0])/2,
        (a[1] + b[1])/2
    ]

    // Make the midpoint the origin
    a_mid = [
        a[0] - midpoint[0],
        a[1] - midpoint[1]
    ]
    b_mid = [
        b[0] - midpoint[0],
        b[1] - midpoint[1]
    ]

    // Use the rotation matrix from the paper you mentioned
    a_rotated = [
        cos(angle)*a_mid[0] - sin(angle)*a_mid[1],
        sin(angle)*a_mid[0] + cos(angle)*a_mid[1]
    ]
    b_rotated = [
        cos(angle)*b_mid[0] - sin(angle)*b_mid[1],
        sin(angle)*b_mid[0] + cos(angle)*b_mid[1]
    ]

    // Then add the midpoint coordinates to return to previous origin
    a_rotated[0] = a_rotated[0] + midpoint[0]
    a_rotated[1] = a_rotated[1] + midpoint[1]
    b_rotated[0] = b_rotated[0] + midpoint[0]
    b_rotated[1] = b_rotated[1] + midpoint[1]

    // And the rotation is now done
    //return [a_rotated, b_rotated]
  	line(a_rotated[0],a_rotated[1],b_rotated[0],b_rotated[1])
		
}

</script>
