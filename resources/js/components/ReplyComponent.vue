<template>
	<div class="mt-3 mb-3" style="padding-left: 100px;position: relative;">
		<div class="line_cmt"></div>
		<div class="row">
		<div class="col-lg-2 col-md-12 col-sm-12 p-0">
			<div class="div_info_post info_post_mobile">
				<div class="forum_info_auth info_user_reply" :style="{backgroundImage:'url(./'+reply.avatar+')'}" style="border-radius:50%;background-position: center;background-size: cover;border:1px solid #ccc" ></div>
				<div class="div_level_user">
					<a class="link_user" style="font-weight: 500;margin-right: 4px" status="false" :username="reply.id" href="">{{reply.displayname}}
					<div class="user_name"></div>
					</a>
				</div>
			</div>
		</div>
		<div style="background: #D9D7D7" class="col-lg-10 alert p-2">
			<div style="display: flex;justify-content: flex-end;font-size: 0.8rem">
				#{{reply.id_cmt}} | <span class="getTime">{{reply.created_at}}</span>
			</div>
			<div v-html="reply.content_cmt" :id="'cmt_forum_'+reply.id_cmt" style="min-height: 40px" class="cmt_forum">
				
			</div>
			<div class="url">
				<link-prevue :url="getLink">
					<template slot-scope="props">
						<a v-bind:href="props.url">
				      <div class="card" style="width: 20rem;">
				        <img class="card-img-top" :src="props.img" :alt="props.title" />
				        <div class="card-block">
				          <h4 class="card-title">{{props.title}}</h4>
				          <p class="card-text">{{props.description}}</p>
				        </div>
				      </div>
				      </a>
				    </template>
				</link-prevue>
				<br>
				<button style="line-height: 1;width: 80px" class="btn btn-info btn-sm">Like!</button>
			</div>
			<div style="display: flex;justify-content: flex-end;">
				<i v-on:click="formReply" class="fas fa-reply btn_reply"></i>
			</div>
		</div>
	</div>
	</div>
</template>

<script>
import LinkPrevue from 'link-prevue'
export default {

  name: 'ReplyComponent',
  props:{
  	reply:Object
  },
  data () {
    return {

    }
  },
  components:{
  	LinkPrevue
  },
  computed:{
  	getLink(){
  		return this.reply.content_cmt.match(/\bhttps?:\/\/\S+/gi)[0];
  	}
  },
  methods:{
  	formReply(){
  		this.$emit('formReply');
  	}
  }
}
</script>

<style lang="css" scoped>
.url p{
	line-height: unset; 
    letter-spacing: unset;
}
.url h4{
	margin-bottom:4px;
}
.url{
	color:black;
}
</style>