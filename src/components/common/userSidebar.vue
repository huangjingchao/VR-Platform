<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" id="navigator" theme="dark" unique-opened router>
            <template v-for="item in items">
                <template v-if="item.subs">
                    <el-submenu :index="item.index">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                hello:"hahahaha",
                items: [
                    {
                        icon: 'el-icon-menu',
                        index: '1',
                        title: 'VR资讯',
                        subs: [
                            {
                                index: '/user/news-list',
                                title: '新闻资讯'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-setting',
                        index: '2',
                        title: '个人信息管理',
                        subs: [
                            {
                                index: '/user/change-nick',
                                title: '修改昵称'
                            },
                            {
                                index: '/user/change-password',
                                title: '修改密码'
                            }
                        ]
                    }
                ]
            }
        },
        computed:{
            onRoutes(){
                // return this.$route.path.replace('/','');
            }
        }
    }
</script>

<style scoped>
    .sidebar{
        display: block;
        position: absolute;
        width: 250px;
        left: 0;
        top: 70px;
        bottom:0;
        background: #2E363F;
    }
    .sidebar > ul {
        height:100%;
    }

</style>
