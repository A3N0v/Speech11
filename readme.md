
![互联网并非法外之地](

## 使用方法

### 创建任务

POST https://nthesizer.herokuapp.com/task

Body

```json
{
	"text":"请输入的文字（1000字以内）。支持简体、繁體 ji2 dai4 sheng1 diao4 pin1 yin1."
}
```

Response

```json
{
    "id": "55892d29-cec6-495f-b2b3-3139534efaac",
    "request_successful": true
}
```

### 查询进度

GET  https:/esizer.herokuapp.com/progress?id=55892d29-cec6-495f-b2b3-3139534efaac

Response (查询成功)

```json
{
    "request_successful": true,
    "result": {
        "finished": true,
        "progress": 1.0
    }
}
```

Response (查询失败)

```json
{
    "message": "找不到此项目",
    "request_successful": false
}
```

### 获取音频

GET https:/hesizer.herokuapp.com/result?id=55892d29-cec6-495f-b2b3-3139534efaac

**返回的音频文件经过base64编码，方便嵌入网页前端**

Response (获取成功)

```json
{
    "request_successful": true,
    "result": {
        "audio": "SUQzBAAAAAAAI1RTU0UAAAAPAAADTGF2ZjU4LjI5LjEwMAAAAAAAAAAAAAAA/+OgwAAAAAAAAAAAAEluZm8AAAAPAAAAAwAAB1cAjo6Ojo6Ojo6Ojo6Ojo6Ojo6Ojo6Ojo6Ojo6Ojo6Ojo6OxAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD/44DEAAAAA0gAAAAATEFNRTMuMTAwVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV/+OCxAAAAANIAAAAAExBTUUzLjEwMFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVUxBTUUzLjEwMFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVQ==",
        "message": [
            "找不到音节 biang",
            "找不到音节 duang",
            "找不到音节 biu"
        ],
        "synthesis_successful": true
    }
}
```

Response (获取失败)

```json
{
    "message": "找不到此项目",
    "request_successful": false
}
```

### 删除数据

DELETE  https:/esizer.herokuapp.com/result?id=55892d29-cec6-495f-b2b3-3139534efaac

Response 1

```json
{
    "request_successful": true
}
```

Response 2

```json
{
    "message": "项目已被删除",
    "request_successful": false
}
```

**注意：临时存放在服务器上的音频数据会定时清除。**

## 亲自部署

**请确保 Python 版本在 3.6 以上。**

1. 创建并进入[虚拟环境](https://docs.python.org/zh-cn/3/tutorial/venv.html)

2. 安装 requirements.txt 依赖

   ```bash
   $ pip3 install -r requirements.txt
   ```

3. 安装 [ffmpeg](https://github.com/jiaaro/pydub#getting-ffmpeg-set-up) (用于编码 mp3 文件)

4. 运行 Flask APP

   ```bash
   $ set FLASK_APP=api.py
   $ flask run
   * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
   ```
