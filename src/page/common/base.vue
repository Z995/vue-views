<template>
	<div id="common">
		<div class="layout">
			<Layout>
				<Sider ref="side1" hide-trigger collapsible :collapsed-width="80" v-model="isCollapsed">
					<div class="zyl-layout-log">
						<img src="../../assets/logo.png" alt="">
						<span v-if="!this.isCollapsed">Admin KD</span>
					</div>
					<Menu :open-names="['1']" accordion theme="dark" width="auto" :class="menuitemClasses">
						<div v-if="!this.isCollapsed">
							<Submenu name="1">
								<template slot="title">
									<Icon type="ios-paper" />
									<span>内容管理</span>
								</template>
								<MenuItem name="1-1">文章管理</MenuItem>
								<MenuItem name="1-2">评论管理</MenuItem>
								<MenuItem name="1-3">举报管理</MenuItem>
							</Submenu>
							<Submenu name="2">
								<template slot="title">
									<Icon type="ios-people" />
									<span>用户管理</span>
								</template>
								<MenuItem name="2-1">新增用户</MenuItem>
								<MenuItem name="2-2">活跃用户</MenuItem>
							</Submenu>
							<Submenu name="3">
								<template slot="title">
									<Icon type="ios-stats" />
									<span>统计分析</span>
								</template>
								<MenuGroup title="使用">
									<MenuItem name="3-1">新增和启动</MenuItem>
									<MenuItem name="3-2">活跃分析</MenuItem>
									<MenuItem name="3-3">时段分析</MenuItem>
								</MenuGroup>
								<MenuGroup title="留存">
									<MenuItem name="3-4">用户留存</MenuItem>
									<MenuItem name="3-5">流失用户</MenuItem>
								</MenuGroup>
							</Submenu>
						</div>
						<div v-else>
							<Dropdown placement="left-end">
								<Icon type="ios-paper" />
								<DropdownMenu slot="list">
									<DropdownItem>文章管理</DropdownItem>
									<DropdownItem>评论管理</DropdownItem>
									<DropdownItem>举报管理</DropdownItem>
								</DropdownMenu>
							</Dropdown>
							<Dropdown placement="left-end">
								<Icon type="ios-people" />
								<DropdownMenu slot="list">
									<DropdownItem>文章管理</DropdownItem>
									<DropdownItem>评论管理</DropdownItem>
									<DropdownItem>举报管理</DropdownItem>
								</DropdownMenu>
							</Dropdown>
							<Dropdown placement="left-end">
								<Icon type="ios-people" />
								<DropdownMenu slot="list">
									<DropdownItem>文章管理</DropdownItem>
									<DropdownItem>评论管理</DropdownItem>
									<DropdownItem>举报管理</DropdownItem>
								</DropdownMenu>
							</Dropdown>
						</div>
					</Menu>
					
				</Sider>
				<Layout :class="collapsedHeader" class="zyl-layout-right">
					<Header class="layout-header-bar">
						<Icon @click.native="collapsedSider" :class="rotateIcon" :style="{ margin: '0 20px' }" type="md-menu" size="24"></Icon>
					</Header>
					<Content class="zyl-content" :style="{ margin: '20px', background: '#fff', minHeight: '260px' }">Content</Content>
				</Layout>
			</Layout>
		</div>
	</div>
</template>
<script>
export default {
        data () {
            return {
                isCollapsed: false
            }
        },
        computed: {
            rotateIcon () {
                return [ 'menu-icon', this.isCollapsed ? 'rotate-icon' : '' ];
            },
            menuitemClasses () {
                return [ 'menu-item', this.isCollapsed ? 'collapsed-menu' : '' ]
            },
			collapsedHeader(){
				return [this.isCollapsed ? 'collapsed-header' : '' ]
			}
        },
        methods: {
            collapsedSider () {
                this.$refs.side1.toggleCollapse();
            }
        }
    }
</script>

<style lang="less">
	.layout-header-bar{
		background: #fff;
		padding: 0 !important;
	}
	.zyl-layout-right{
		top: 0;
		width: 100%;
		height: 100%;
		z-index: 11;
		position: fixed;
		padding-left: 200px;
		transition: all .3s ease-in-out;
	}
	.collapsed-header{
		padding-left: 80px !important;
	}
	.ivu-layout-sider{
		position: fixed;
		height: 100%;
		z-index: 999;
		transition: all .3s ease-in-out;
	}
	.ivu-menu-submenu-title{
		overflow:  hidden;
		white-space: nowrap;
	}
	
	/* logo */
	.zyl-layout-log{
		width: 100%;
		text-align: center;
		height: 64px;
		color: #fff;
		
		img{
			width: 40px;
			height: 40px;
			position: relative;
			top: 15px;
		}
		
	}
	
	.ivu-dropdown{
		width: 100%;
		display: block;
		height: 50px;
		line-height: 50px;
		text-align: center;
		color: #cbcecd;
		
		.ivu-select-dropdown{
			width: auto !important;
		}
	}
	
</style>
