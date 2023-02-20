launchApp("淘宝");

sleep(500);

for(;;){
    
    if(className("FrameLayout").depth(14).desc("签到").exists()){
        
        className("FrameLayout").depth(14).desc("签到").findOne().click();
        
        break;
    }
}

threads.start(function(){

    tanchuang();

});

text('连续签到领元宝').waitFor();

sleep(3000);

if(text("立即签到").exists()){

    sleep(200);

    text("立即签到").findOne().parent().parent().click();

};

sleep(2000);

var zhuanyuanbao = className("android.widget.Image").text("O1CN01hRBLil20KeKWCH7Z0_!!6000000006831-2-tps-104-115").findOne().parent().parent();

for(;;){
    
    sleep(3000);

    text("连续签到领元宝").waitFor()
    
    sleep(1000);
    
    zhuanyuanbao.click();
    
    sleep(5000);

    if(!text("去逛逛").exists()){

        break;

    }
    
    text("去逛逛").click();
    
    sleep(2000);
    
    swipe(500,900,500,300,500);
    
    sleep(16000);
    
    swipe(500,900,500,300,500);
    
    sleep(16000);
    
    back();
    
    sleep(5000);

}

if(textContains("去搜索").exists()){

    sousuo();

}

sleep(1000);

back();

sleep(200);

back();

sleep(200);

device.vibrate(1000);

toast('完成了');



function sousuo(){

    sleep(2000);

    className("android.widget.ListView").findOne().children().forEach(child => {
        var target = child.findOne(className("android.widget.Button"));
        target.click();
    });

    sleep(2000);

    sleep(2000);

    click(155, 398);

    sleep(2000);

    swipe(500, 900, 500, 300, 500);

    sleep(20000);

    swipe(500, 900, 500, 300, 500);

    sleep(20000);

    back();

    sleep(500);

    back();

}

function tanchuang(){

    while(true){

        //签到后的弹窗
        if (textContains("立即领").exists()) {

            var anniu = textContains("立即领").findOne().parent().parent().child(3);

            anniu.click();

        };

        //30秒后的弹窗
        if (textContains("去使用").exists()) {

            var anniu = textContains("去使用").findOne().parent().parent().child(2).child(0);

            anniu.click();

        };

    };
    
};
