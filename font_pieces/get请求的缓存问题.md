1. 场景， 当发请求时， 返回结果为304

2. 在ajax请求是添加 cache: false;

    ```
    index: (data = {}, callback) => {
            this.fetch({
                url: this.api.dept.index,
                method: 'get',
                cache: false,
                data
            }, data => {
                callback(data);
            });
        },
    ```
3. 在发送请求时添加随机数
    ```
    let rand = {
        rand: Math.random()
    };
    API.dept().index(rand, data => {
        console.log(data);
    });
    ```
    