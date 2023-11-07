<template>
    <div class="card">
        <div class="crad-body">
            <div class="row">
                <div class="col-3">
                    <img class="img-fluid" src="https://cdn.acwing.com/media/user/profile/photo/63001_lg_52db80a3df.jpg" alt=""> 
                </div>
                <div class="col-9">
                    <div class="username">{{ fullName }}</div>
                    <div class="fans">粉丝:{{ user.followerCount }}</div>
                    <button @click="follow" v-if="!user.is_followed" type="button" class="btn btn-secondary btn-sm">+关注</button>
                    <button @click="unfollow" v-if="user.is_followed" type="button" class="btn btn-secondary btn-sm">取消关注</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { computed } from 'vue';

export default {
    name:"UserProfileInfo",
    props: {
        user: {
            type: Object,
            required: true,
        }
    },

    setup(props, context) {
        let fullName = computed(()=>props.user.username)
        const follow = () => {
            context.emit('follow')
        }

        const unfollow = () => {
            context.emit('unfollow')
        }
        
        // console.log(1)
        // console.log(fullName)
        // console.log(2)
        return {
            fullName,
            follow,
            unfollow
        }
    }
}
</script>

<style scoped>
img {
    border-radius: 50%;
}

.username {
    font-weight: bold;
}
.fans{
    font-size: 12px;
    color:gray;
}

button {
    padding: 2px 4px;
    font-size: 12px;
}
</style>