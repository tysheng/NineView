# NineView
类似微信朋友圈的九图,List为空时自动隐藏，1-9图自动识别，只需简单继承和使用
[地址](https://gist.github.com/tysheng/be2f61acca1f31b9ebd851b5222bdb8a)
##使用
使用方法很简单
###第一步
###直接继承 NineView，实现两个方法
```java
    loadIntoImage(String url, ImageView imageView);
    initImageView();
```
比如
```java
public class MyNineView extends NineView {
    public MyNineView(Context context) {
        super(context);
    }

    @Override
    protected void loadIntoImage(String url, ImageView imageView) {
        //使用你所在用的图片加载器
        //以Glide为例
        Glide.with(mContext).load(url).into(imageView);
    }

    @Override
    protected ImageView initImageView() {
        //新建一个ImageView
        return new ImageView(mContext);
        //或者使用点击特效的PressDarkImageView
        //return new PressDarkImageView(mContext);
    }
}
```
###第二步
###在Activity/Adapter中使用
```java
    //传入List<String>，String为图片的url
    myNineView.setList(mList);
    //第二个参数可选，设置imageview之间的padding，默认是3
    //myNineView.setList(mList,3);
    myNineView.setOnItemClickListener(new NineView.OnItemClickListener() {
            @Override
            public void onItemClick(View view, int position, List<String> mList) {
                //do your things
            }
        });    
```
