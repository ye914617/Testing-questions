# Testing-questions
Interview testing questions for Welly


1. 建立函式 fibonacci 代入參數 position，position 表示的是想要得到 fibonacci sequence 中的第幾個數字的值。

 fibonacci(0) // 0
 fibonacci(1) // 1
 fibonacci(2) // 1
 fibonacci(3) // 2
 fibonacci(4) // 3 

Answer:
--------

const fibonacciNum = function(n) {
    const arr = [0,1];
    if(n<2) {
        return arr[n]
    }
    for(let i =2;i<=n;i++){
        arr.push(arr[i-1]+arr[i-2])
    }
    return arr[arr.length-1]
    
};

---------------------------------------------------------------------------------

2. 使用 Linked List 實作 Stack ，實作需包含以下方法。
 push() : 添加新元素。 pop():移除元素並返回被移除的元素。 size():返回所有元素數量。 
				
const stack = new Stack() 
stack.push(1)
stack.push(2) 
stack.push(3) 
stack.pop() // 3 
stack.size() // 2 

Answer:
--------

const MyStack = function () {
  this.queue = [];
};

MyStack.prototype.push = function (x) {
  this.queue.push(x);
  for (let i = 1; i < this.queue.length; i++) {
    this.queue.push(this.queue.shift());
  }
  console.log(this.queue);
};

MyStack.prototype.pop = function () {
  return this.queue.shift();
};

MyStack.prototype.size = function () {
  console.log(this.queue.length);
  return this.queue.length;
};

---------------------------------------------------------------------------------

3.將下列輸入資料整合成期望的輸出結果。

Answer:
--------

function dataHandling() {
  const result = userIds.map((item) => {
    const getOrderId = userOrders
      .filter((getid) => {
        if (item === getid.userId) {
          return getid;
        }
      })
      .map((getord) => {
        return getord.orderIds;
      })
      .map((ordid) => {
        for (const key2 in orderData) {
          if (ordid.includes(key2)) {
            return {
              id: key2,
              name: orderData[key2].name,
              price: orderData[key2].price,
            };
          }
        }
      });

    for (const key in userData) {
      if (item === key) {
        return {
          user: {
            id: key,
            name: userData[key],
          },
          order: getOrderId,
        };
      }
    }
  });
  console.log(result);
}

dataHandling();
