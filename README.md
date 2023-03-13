# Binding Adapter For ImageView

Setting text from data class to XML layout through dataBinding is quite easy,

But If you want to set image directly from your data class to your XML layout through dataBinding , then you have to make an adapter file :



In that file you can define an extra custom function for your views i.e. : ImageView or TextView.



Here we need to define an extra function for our ImageView so that we can directly load image from URL into our XML layout.



Now follow below steps :



	1) Create an data class and initialise it in your main activity. data class example :               
	
	data class Post(val title: String, val description: String, val url: String)

	

	Initialise it in mainActivity.kt 

	Val post = Post("this is title", "this is description", "this is  Image URL")

	binding.variable = post

	

	2) Now create an Adapter.kt file and define an extra function for our ImageView  :-                   

	

	 @BindingAdapter("imageFromUrl")

	 fun ImageView.imageFromUrl(url: String){   

	  Glide.with(this.context).load(url).into(this)

	}    

	

	Now here you created an extra feature/function for your ImageView , You can close this adapter file and let's move on to our XML layout , here in your ImageView write -

	

	android:imageFromUrl= "@{post.url}"

	

	and that's it run the application and you are now able to set image directly from your data class in your XML layout
