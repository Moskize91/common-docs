# 自定义事件

根据你自己的业务逻辑，可以定义自定义事件广播全房间。通过如下代码，可以发送自定事件。

{% tabs %}
{% tab title="JavaScript" %}
```javascript
var event = "ChatMessage"; // 取一个合适的自定义事件名称
var payload = {...}; // 事件荷载，由事件附带，根据业务逻辑自行设计

room.dispatchMagixEvent(event, payload);
```
{% endtab %}
{% endtabs %}

通过如下代码，可以接受房间里其他人发送的自定义事件。

{% tabs %}
{% tab title="JavaScript" %}
```javascript
var event = "ChatMessage"; // 你希望监听的自定义事件名称

room.addMagixEventListener(event, onReceivedChatMessage);

function onReceivedChatMessage(event) {
    console.log(event.payload); // 接收到事，并打印出来
}
```
{% endtab %}
{% endtabs %}

当不再希望接收某个自定义事件时，可以通过如下代码注销监听。

{% tabs %}
{% tab title="JavaScript" %}
```javascript
var event = "ChatMessage"; // 你希望注销监听的自定义事件名称
room.removeMagixEventListener(event, onReceivedChatMessage);
```
{% endtab %}
{% endtabs %}

