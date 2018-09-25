# vueComponent
0927 homework
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>우리가 어떤 민족입니까</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>
  <div id="app" class="container py-5">
    <div class="row">
      <div class="card-deck">
        <div class="col-md-4 card mb-3 px-0" v-for="thing in things">
          <img class="card-img-top" :src="thing.src" alt="Card image cap">
          <div class="card-body">
            <h5 class="card-title">{{ thing.title }}</h5>
            <p class="card-text">{{ thing.text }}</p>
            <p class="card-text"><small class="text-muted">1분전 업데이트 됨</small></p>
            <a href="#" class="btn btn-primary" @click="addTotal(thing.id)">장바구니에 담기</a>
          </div>
        </div>
      </div>
      <div class="col-12 px-0 card text-center">
          <div class="card-header">
            장바구니 목록
          </div>
          <div class="card-body text-left">
            <h5 class="card-title">다음을 구매하십니까?</h5>
            <ul>
              <li v-for="thing in things" class="card-text">{{thing.title}} {{thing.total}}개</li> 
            </ul>
            <a href="#" class="btn btn-warning float-right" @click="backZero">장바구니 초기화</a>
          </div>
        </div>
      </div>
    </div>

  <script>
     const app =  new Vue({
          el: '#app',
          data: {
              things: [
                  { 
                  id: 0, 
                  src: './assets/images/coffee.jpg', 
                  title: '커피커피', 
                  text: '커피 또는 커피차는 커피나무의 씨를 볶아 가루로 낸 것을 따뜻한 물과 차가운물 또는 증기로 우려내어 마시는 쓴맛이 나는 음료이다.',
                  total: 0 
                  },
                  {
                  id: 1, 
                  src: './assets/images/fruit.jpg', 
                  title: '베리베리', 
                  text: '과일 은 나무나 초본 식물에 달리는, 먹을 수 있는 열매를 가리킨다. 일반적으로 열매 부분은 버리고 씨만을 식용하는 호두는 과일로 치지 않는다.',
                  total: 0
                  },
                  { 
                  id: 2, 
                  src: './assets/images/meat.jpg', 
                  title: '고기고기', 
                  text: '고기는 동물의 살점, 특히 인간이 먹는 동물의 살을 이르는 말이다. 육류, 식육이라고도 한다. 맛있다.',
                  total: 0
                  }
                  ]
                },
          methods: {
          addTotal(id){
              this.things[id].total += 1
          },
          backZero(){
              this.things.forEach(thing => {thing.total = 0})
          }
        }
      })
     
  </script>
</body>
</html>
