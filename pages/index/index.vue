<template>
	<view class="body">
		<view id="qipan">
			<!-- <image   src="../../static/img/stype_1/bg.png"> -->
			<canvas id="bg" canvas-id="canvas" @touchend="go"></canvas>
			<!-- </image> -->
		</view>
		<view class="bottom">
			<view class="button">
				<button value='返回' @click="fanHui">返回</button>
			</view>
			<view class="button">
				<button value='悔棋' @click="huiQi">悔棋</button>
			</view>
		</view>
	</view>
</template>

<script>
	// var canMovejs=require('../pageJS/CanMove.js');
	// var init=require('../pageJS/draw.js')
	export default {
		data() {
			return {
				screenWidth: 0, //获取屏幕的宽度
				screenHeight: 0, //获取屏幕的高度
				qipanshangdeqizi: [],
				buzhou: [],
				leave:3,
				selectId: -1,
				bRedTurn: true,
				wd: 0,
				wh: 0,
				page:'',
				isRoot:false,
				qizi: [{
						id: 0,
						death: false,
						red: false,
						type: "车",
						row: 0,
						col: 0,
						image: '../../static/img/stype_1/b_c.png',
						value:100,
					}, {
						id: 1,
						death: false,
						red: false,
						type: '马',
						row: 0,
						col: 1,
						image: '../../static/img/stype_1/b_m.png',
						value:50,
					}, {
						id: 2,
						death: false,
						red: false,
						type: '相',
						row: 0,
						col: 2,
						image: '../../static/img/stype_1/b_x.png',
						value:10,
					}, {
						id: 3,
						death: false,
						red: false,
						type: '士',
						row: 0,
						col: 3,
						image: '../../static/img/stype_1/b_s.png',
						value:10,
					}, {
						id: 4,
						death: false,
						red: false,
						type: '将',
						row: 0,
						col: 4,
						image: '../../static/img/stype_1/b_j.png',
						value:1500,
					}, {
						id: 5,
						death: false,
						red: false,
						type: "士",
						row: 0,
						col: 5,
						image: '../../static/img/stype_1/b_s.png',
						value:10,
					}, {
						id: 6,
						death: false,
						red: false,
						type: "相",
						row: 0,
						col: 6,
						image: '../../static/img/stype_1/b_x.png',
						value:10,
					}, {
						id: 7,
						death: false,
						red: false,
						type: "马",
						row: 0,
						col: 7,
						image: '../../static/img/stype_1/b_m.png',
						value:50,
					}, {
						id: 8,
						death: false,
						red: false,
						type: "车",
						row: 0,
						col: 8,
						image: '../../static/img/stype_1/b_c.png',
						value:100,
					}, {
						id: 9,
						death: false,
						red: false,
						type: "炮",
						row: 2,
						col: 1,
						image: '../../static/img/stype_1/b_p.png',
						value:50,
					}, {
						id: 10,
						death: false,
						red: false,
						type: "炮",
						row: 2,
						col: 7,
						image: '../../static/img/stype_1/b_p.png',
						value:50,
					}, {
						id: 11,
						death: false,
						red: false,
						type: "兵",
						row: 3,
						col: 0,
						image: '../../static/img/stype_1/b_z.png',
						value:20,
					}, {
						id: 12,
						death: false,
						red: false,
						type: "兵",
						row: 3,
						col: 2,
						image: '../../static/img/stype_1/b_z.png',
						value:20,
					}, {
						id: 13,
						death: false,
						red: false,
						type: "兵",
						row: 3,
						col: 4,
						image: '../../static/img/stype_1/b_z.png',
						value:20,
					}, {
						id: 14,
						death: false,
						red: false,
						type: "兵",
						row: 3,
						col: 6,
						image: '../../static/img/stype_1/b_z.png',
						value:20,
					}, {
						id: 15,
						death: false,
						red: false,
						type: "兵",
						row: 3,
						col: 8,
						image: '../../static/img/stype_1/b_z.png',
						value:20,
					},
					{
						id: 16,
						death: false,
						red: true,
						type: "车",
						row: 9,
						col: 0,
						image: '../../static/img/stype_1/r_c.png',
						value:100,
					}, {
						id: 17,
						death: false,
						red: true,
						type: '马',
						row: 9,
						col: 1,
						image: '../../static/img/stype_1/r_m.png',
						value:50,
					}, {
						id: 18,
						death: false,
						red: true,
						type: '相',
						row: 9,
						col: 2,
						image: '../../static/img/stype_1/r_x.png',
						value:10,
					}, {
						id: 19,
						death: false,
						red: true,
						type: '士',
						row: 9,
						col: 3,
						image: '../../static/img/stype_1/r_s.png',
						value:10,
					}, {
						id: 20,
						death: false,
						red: true,
						type: '将',
						row: 9,
						col: 4,
						image: '../../static/img/stype_1/r_j.png',
						value:1500,
					}, {
						id: 21,
						death: false,
						red: true,
						type: "士",
						row: 9,
						col: 5,
						image: '../../static/img/stype_1/r_s.png',
						value:10,
					}, {
						id: 22,
						death: false,
						red: true,
						type: "相",
						row: 9,
						col: 6,
						image: '../../static/img/stype_1/r_x.png',
						value:10,
					}, {
						id: 23,
						death: false,
						red: true,
						type: "马",
						row: 9,
						col: 7,
						image: '../../static/img/stype_1/r_m.png',
						value:50,
					}, {
						id: 24,
						death: false,
						red: true,
						type: "车",
						row: 9,
						col: 8,
						image: '../../static/img/stype_1/r_c.png',
						value:100,
					}, {
						id: 25,
						death: false,
						red: true,
						type: "炮",
						row: 7,
						col: 1,
						image: '../../static/img/stype_1/r_p.png',
						value:50,
					}, {
						id: 26,
						death: false,
						red: true,
						type: "炮",
						row: 7,
						col: 7,
						image: '../../static/img/stype_1/r_p.png',
						value:50,
					}, {
						id: 27,
						death: false,
						red: true,
						type: "兵",
						row: 6,
						col: 0,
						image: '../../static/img/stype_1/r_z.png',
						value:20,
					}, {
						id: 28,
						death: false,
						red: true,
						type: "兵",
						row: 6,
						col: 2,
						image: '../../static/img/stype_1/r_z.png',
						value:20,
					}, {
						id: 29,
						death: false,
						red: true,
						type: "兵",
						row: 6,
						col: 4,
						image: '../../static/img/stype_1/r_z.png',
						value:20,
					}, {
						id: 30,
						death: false,
						red: true,
						type: "兵",
						row: 6,
						col: 6,
						image: '../../static/img/stype_1/r_z.png',
						value:20,
					}, {
						id: 31,
						death: false,
						red: true,
						type: "兵",
						row: 6,
						col: 8,
						image: '../../static/img/stype_1/r_z.png',
						value:20,
					}
				], //初始化所有的棋子
			}
		},


		mounted() {

		},
		methods: {
			
			init() {
				//获取屏幕的宽度和高度；
				var SystemInfo = uni.getSystemInfoSync({
					success: function(res) {
						console.log("成功", res)
					}
				});
				this.screenWidth = SystemInfo.windowWidth;
				this.screenHeight = SystemInfo.windowHeight - 100;
				//定义宽度和高度
				var width = this.screenWidth;
				var height = this.screenHeight;
				//创建画布
				var context = uni.createCanvasContext('canvas', this);
				//在画布上画图片  棋盘
				// context.drawImage('../../static/img/stype_1/bg.png',0,0,width,height)
				var hd = height / 10;
				this.wh = hd;
				var wd = width / 9;
				this.wd = wd;


				//画九条竖线
				for (let i = 0; i < 9; i++) {
					if (i == 0 || i == 8) {
						context.moveTo((wd / 2) + wd * i, hd / 2);
						context.lineTo((wd / 2) + wd * i, hd * 9 + hd / 2)
						context.stroke();
					} else {
						context.moveTo((wd / 2) + wd * i, hd / 2);
						context.lineTo((wd / 2) + wd * i, hd * 4 + hd / 2)
						context.stroke();
						context.moveTo((wd / 2) + wd * i, hd * 5 + hd / 2);
						context.lineTo((wd / 2) + wd * i, hd * 9 + hd / 2)
						context.stroke();
					}

				}
				//画十条横线
				for (let i = 0; i < 10; i++) {
					context.moveTo((wd / 2), hd / 2 + hd * i);
					context.lineTo((wd / 2) + wd * 8, hd / 2 + hd * i);
					context.stroke()
				}
				//画九宫格
				// 上边的九宫格
				context.moveTo((wd / 2) + wd * 3, hd / 2);
				context.lineTo((wd / 2) + wd * 5, hd * 2 + hd / 2)
				context.stroke();
				context.moveTo((wd / 2) + wd * 5, hd / 2);
				context.lineTo((wd / 2) + wd * 3, hd * 2 + hd / 2)
				context.stroke();
				// 下边的九宫格
				context.moveTo((wd / 2) + wd * 5, hd * 7 + hd / 2);
				context.lineTo((wd / 2) + wd * 3, hd * 9 + hd / 2)
				context.stroke();
				context.moveTo((wd / 2) + wd * 5, hd * 9 + hd / 2);
				context.lineTo((wd / 2) + wd * 3, hd * 7 + hd / 2)
				context.stroke();

				//在棋盘上画棋子
				for (var i = 0; i < 32; i++) {
					var curryqizi = this.qizi[i];
					if (!curryqizi.death) { //如果棋子已经死了 就不会在棋盘上显示出来。
						var point = this.getPoint(curryqizi.row, curryqizi.col);
						context.drawImage(curryqizi.image, point.x, point.y, wd, hd);
					}

				}
				// 如果是第一次选中就在棋子的周围画上四角符号。
				if (this.selectId != -1) {
					var selectStone = this.qizi[this.selectId];
					var point = this.getPoint(selectStone.row, selectStone.col);
					context.drawImage('../../static/img/stype_1/b_box.png', point.x, point.y, wd, hd);
				}
				context.draw()
			},
			
		   AIMove(){
			   var step=this.computerMove();
			   	console.log('电脑步骤：',step);
				if(step.killedId!=-1){
					this.qizi[step.killedId].death=true;
				} 
				console.log(this.qizi[step.movedId]);
			   	this.moveStone(step.movedId,step.toRow,step.toCol);
			   	this.buzhou.push(step);
				this.selectId = -1;
			   	this.bRedTurn = !this.bRedTurn;
			    this.init();
		   },
		   //走棋子的函数
		   goStone(e){
			   // 获取点击的坐标点
			   var x = e.changedTouches[0].x;
			   var y = e.changedTouches[0].y;
			   var canGoStone = this.getRowCol(x, y); //根据坐标点找到相应的行列坐标
			   if (!canGoStone.bol) {
					return;
			   }
			   var row = canGoStone.row;
			   var col = canGoStone.col;
			   var i;
			   var clickid = -1;
			   var qizi = this.qizi;
			   // 遍历数组判断是不是选中了棋子。
			   for (i = 0; i < 32; ++i) {
					if (qizi[i].row == row && qizi[i].col == col && qizi[i].death == false) {
						clickid = i;
						console.log(this.qizi[i].type,'clickid',i);
						break;
					}
			   }
			   var _selectid = this.selectId;
			   // 如果是-1表示第一次点击
			   if (_selectid == -1) {
					// 不是-1表示点击的这个是个棋子
					if (clickid != -1) {
						// 轮流走棋规则  
						if (this.bRedTurn == qizi[clickid].red) {
							this.selectId = clickid;
						}
						this.init();
					}	
			   } else {
						// 或者 已经不是第一次了 是第二次 已经选中了棋子
						//添加规则 如果可以走
						if (this.canMove(_selectid, row, col, clickid)) {
							var beforMoveRow = this.qizi[_selectid].row;
							var beforMoveCol = this.qizi[_selectid].col;
							this.qizi[_selectid].row = row;
							this.qizi[_selectid].col = col;
							// 如果不是-1表示是吃子。
							if (clickid != -1 && clickid != _selectid) {
								this.qizi[clickid].death = true;
							}
							this.selectId = -1;
							var isred=this.bRedTurn;
							this.bRedTurn = !this.bRedTurn;
							this.init();
							
							// 将吃子的步骤放到步骤里
							var buzhou = {
								killedId: clickid,
								movedId:_selectid,
								moveRow: beforMoveRow,
								moveCol: beforMoveCol,
								toRow: row,
								toCol: col,
								isred:isred,
							}
							this.buzhou.push(buzhou);
						}
					}
					/*下边代码是添加背景音乐的代码*/
					
					const innerAudioContext = uni.createInnerAudioContext();
					innerAudioContext.autoplay = true;
					//播放背景音乐
					if (_selectid == -1) {
						innerAudioContext.src = '../../static/bgm/提起棋子的声音.mp3';
						innerAudioContext.onPlay(() => {
							console.log('开始播放提起棋子的声音');
						});
						innerAudioContext.onError((res) => {
							console.log(res.errMsg);
							console.log(res.errCode);
						});
					} else {
						innerAudioContext.src = '../../static/bgm/走子的声音.m4a';
					
						innerAudioContext.onPlay(() => {
							console.log('开始播放走子的声音');
						});
						// if (innerAudioContext.currentTime == 1.000000) {
						// 	innerAudioContext.onStop(function() {
						// 		console.log("停止播放走子的声音");
						// 	})
						// }
						innerAudioContext.onError((res) => {
							console.log(res.errMsg);
							console.log(res.errCode);
						});
					}
					var that=this;
					if(this.qizi[4].death){
						uni.showModal({
							title: '红棋胜利^_^',
							content: '黑棋被将军死棋',
							success: function (res) {
								if (res.confirm) {
									console.log('用户点击确定');
									that.fanHui();
								} else if (res.cancel) {
									console.log('用户点击取消');
									that.fanHui();
								}
							}
						});
					}
					if(this.qizi[20].death){
						uni.showModal({
							title: '黑棋胜利^_^',
							content: '红棋被将军死棋',
							success: function (res) {
								if (res.confirm) {
									console.log('用户点击确定');
									that.fanHui();
								} else if (res.cancel) {
									console.log('用户点击取消');
									that.fanHui();
								}
							}
						});
					}
				
		   },
			//走棋点击事件
			go(e) {
				this.goStone(e);
				if(this.isRoot&&!this.bRedTurn){
					 this.AIMove()
				}
			},
			// 走棋  --- 根据坐标点得到行列是 返回一个点 包含行列坐标 还有 是否在棋盘内。
			getRowCol(x, y) {
				var point = {
					bol: false,
					row: 0,
					col: 0
				};
				for (var row = 0; row <= 9; row++) {
					for (var col = 0; col <= 8; col++) {
						var pt = this.getPoint(row, col);
						var dx = x - pt.x;
						var dy = y - pt.y;
						var dist = dx * dx + dy * dy;
						if (dist < this.wd * this.wh) {
							point.bol = true;
							point.row = row;
							point.col = col;
							return point;
						}
					}
				}
				return point;
			},
			// 根据行列返回对应的点；
			getPoint(row, col) {
				//定义宽度和高度
				var width = this.screenWidth;
				var height = this.screenHeight;
				var wd = width / 9;
				var hd = height / 10;
				var point = {
					x: 0,
					y: 0
				};
				point.x = wd * col;
				point.y = hd * row;
				return point;
			},
			canMove(moveid, row, col, killid) {
				//第一步 如果颜色相同表示 是一伙的 就可以换选择
				if (killid != -1 && this.qizi[moveid].red == this.qizi[killid].red) {
					//换选择
					this.selectId = killid;
					this.init();
					return false;
				}
				switch (this.qizi[moveid].type) {
					case '车':
						return this.canMoveCHE(moveid, row, col, killid);
						break;
					case '马':
						return this.canMoveMA(moveid, row, col, killid);
						break;
					case '相':
						return this.canMoveXIANG(moveid, row, col, killid);
						break;
					case '士':
						return this.canMoveSHI(moveid, row, col, killid);
						break;
					case '将':
						return this.canMoveJIANG(moveid, row, col, killid);
						break;
					case '炮':
						return this.canMovePAO(moveid, row, col, killid);
						break;
					case '兵':
						return this.canMoveBING(moveid, row, col, killid);
						break;
				}
				return true;
			},
			canMoveCHE(moveid, row, col, killid) {
							var stoneMount = this.getStoneMount(moveid, row, col);
							if (this.qizi[moveid].row != row && this.qizi[moveid].col != col) return false;
							if (stoneMount.last && stoneMount.num == 1) return true;
							if (stoneMount.num == 0) return true;
							return false;
						},
						
			canMoveMA(moveid, row, col, killid) {
							var dr = this.qizi[moveid].row - row;
							var drm = false;
							var dc = this.qizi[moveid].col - col;
							var dcm = false
							if (dr < 0) {
								dr = -dr;
								drm = true; //表示往右跳
							}
							if (dc < 0) {
								dc = -dc;
								dcm = true; //表示往下跳
							}
							var d = dr * 10 + dc; //马的时候是12  21  相是22 10 兵的时候是10 1；
							if (d == 12 || d == 21) { //判断马走日字；
								var q = this.qizi;
								// 增加蹩马腿的功能； 往左右跳蹩马腿 
								if (d == 12) {
									if (dcm) {
										var bol = true;
										for (var i = 0; i < 32; i++) {
											if(q[i].death==true)continue;
											if (q[i].row == q[moveid].row && q[moveid].col + 1 == q[i].col) bol = false;
										}
										return bol;
									} else {
										var bol = true;
										for (var i = 0; i < 32; i++) {
											if(q[i].death==true)continue;
											if (q[i].row == q[moveid].row && q[moveid].col - 1 == q[i].col) bol = false;
										}
										return bol;
									}
								} else {
									var q = this.qizi;
									// 增加蹩马腿的功能； 往上下跳蹩马腿 
									if (d == 21) {
										if (drm) { //表示往下跳
											var bol = true;
											for (var i = 0; i < 32; i++) {
												if(q[i].death==true)continue;
												if (q[i].col == q[moveid].col && q[moveid].row + 1 == q[i].row) {
													bol = false;
													break;
											  	}
											}
											return bol;
										} else {
											var bol = true;
											for (var i = 0; i < 32; i++) {
												if(q[i].death==true)continue;
												if (q[i].col == q[moveid].col && q[moveid].row - 1 == q[i].row) bol = false;
											}
											return bol;
										}
									}
									// return true;
								}
								return true;
			
							}
							return false;
						},
			
			canMoveXIANG(moveid, row, col, killid) {
							var dr = row - this.qizi[moveid].row;
							var dc = col - this.qizi[moveid].col;
							var type=this.qizi[moveid].red;
							if(type){
								if(row<4)return false;
							}else{
								if(row>4)return false;
							}
							// 堵象眼
							for (var i = 0; i < 32; i++) {
								if(this.qizi[i].death==true)continue;
								if (this.qizi[i].row == this.qizi[moveid].row + dr / 2 && this.qizi[i].col == this.qizi[moveid].col + dc / 2) {
									return false;
									break;
								}
							}
			
							if (dr < 0) dr = -dr;
							if (dc < 0) dc = -dc;
							var d = dr * 10 + dc; //马的时候是12  21  相是22 10 兵的时候是10 1；
							if (d == 22)
								return true;
			
			
							return false;
						},
			canMoveSHI(moveid, row, col, killid) {
							// 士的游戏规则
							//1.目标位置在九宫格内，
							// 2.移动的步长是一个格子。并且在斜线上
							if (this.qizi[moveid].red) {
								if (row <7) return false;
							} else {
								if (row >2) return false;
							}
							if (col < 3) return false;
							if (col > 5) return false;
			
							var dr = this.qizi[moveid].row - row;
							var dc = this.qizi[moveid].col - col;
							if (dr < 0) dr = -dr;
							if (dc < 0) dc = -dc;
							var d = dr * 10 + dc; //马的时候是12  21  相是22 10 兵的时候是10 1；
							if (d == 11)
								return true;
							return false;
						},
			canMoveJIANG(moveid, row, col, killid) {
							// 将的游戏规则 1.目标位置在九宫格内，
							// 			2.移动的步长是一个格子。
							if (!this.qizi[moveid].red) {
								if (row > 2) return false;
							} else {
								if (row < 7) return false;
							}
							if (col < 3) return false;
							if (col > 5) return false;
			
							var dr = this.qizi[moveid].row - row;
							var dc = this.qizi[moveid].col - col;
							if (dr < 0) dr = -dr;
							if (dc < 0) dc = -dc;
							var d = dr * 10 + dc; //马的时候是12  21  相是22 10 兵的时候是10 1；
							if (d == 1 || d == 10)
								return true;
							return false;
						},
			canMovePAO(moveid, row, col, killid) {
							// 得到要走的棋子中间有多少可以走。
							var stoneMount = this.getStoneMount(moveid, row, col);
							// 要走直线
							if (this.qizi[moveid].row != row && this.qizi[moveid].col != col) return false;
							// 如果中间有一个并且还有最后一个可以走  炮打隔山虎。
							if (stoneMount.last && stoneMount.num == 2) return true;
							// 如果中间没有棋子可以走。
							if (stoneMount.num == 0) return true;
							return false;
						},
			canMoveBING(moveid, row, col, killid) {
							var move_row = this.qizi[moveid].row;
							var move_col = this.qizi[moveid].col;
							var move_red = this.qizi[moveid].red;
							// 判断是红色的棋子还是黑色的棋子
							if (move_red) {
								// 判断是否过河  未过河 只能往前走
								if (move_row >= 5) {
									// 判断是直走
									if (move_col != col) return false;
									// 判断是往前走
									if (row - move_row != -1) return false;
									return true;
								} else {
									// 过河之后不可以往后走
									// if(move_row-row>0)return false;
									if (row == move_row) {
										if (col - move_col == 1 || col - move_col == -1) return true;
										return false;
									} else {
										if (col == move_col) {
											if (row - move_row == -1) return true;
										}
									}
									return false;
								}
			
							} else {
								// 如果是黑色的棋子
								// 判断是否过河  未过河 只能往前走
								if (move_row < 5) {
									// 判断是直走
									if (move_col != col) return false;
									// 判断是往前走
									if (move_row - row != -1) return false;
									return true;
								} else {
									// 过河之后不可以往后走
									// if(move_row-row>0)return false;
									if (row == move_row) {
										if (move_col - col == 1 || move_col - col == -1) return true;
										return false;
									} else {
										if (col == move_col) {
											if (move_row - row == -1) return true;
										}
									}
									return false;
								}
							}
						},
						
			getStoneMount(moveid, row, col) {
				var mount = {
					num: 0,
					last: false
				};
				var q = this.qizi; //将所有棋子的对象拿过来
				// 判断是往列走还是行走
				// 如果是列
				if (q[moveid].col == col) {
					// 找一列中行的个数。
					for (var i = 0; i < 32; i++) {
						if (q[i].death) continue;
						if (q[moveid].row - row < 0) {
							if (q[i].col == col && q[i].row > q[moveid].row && q[i].row <= row) {
								if (q[i].row == row) {
									mount.last = true;
								}
								mount.num += 1;
							};
						} else {
							if (q[i].col == col && q[i].row < q[moveid].row && q[i].row >= row) {
								if (q[i].row == row) {
									mount.last = true;
								}
								mount.num += 1;
							};
						}

					}
				} else {
					// 这是一行中有多少个棋子。
					for (var i = 0; i < 32; i++) {
						if (q[i].death) continue;
						if (q[moveid].col - col < 0) {
							if (q[i].row == row && q[i].col > q[moveid].col && q[i].col <= col) {
								if (q[i].col == col) {
									mount.last = true;
								}
								mount.num += 1;
							};
						} else {
							if (q[i].row == row && q[i].col < q[moveid].col && q[i].col >= col) {
								if (q[i].col == col) {
									mount.last = true;
								}
								mount.num += 1;
							};
						}
					}
				}
				return mount;
			},
			huiQi() {						
				var buzhou=this.buzhou;
				var length=buzhou.length-1;
				if(length==-1)return;
				if(buzhou[length].killedId==-1){
					this.qizi[buzhou[length].movedId].row=buzhou[length].moveRow;
					this.qizi[buzhou[length].movedId].col=buzhou[length].moveCol;
					this.bRedTurn=buzhou[length].isred;
					
				}else{
					this.qizi[buzhou[length].movedId].row=buzhou[length].moveRow;
					this.qizi[buzhou[length].movedId].col=buzhou[length].moveCol;
					this.qizi[buzhou[length].killedId].death=false;
					this.bRedTurn=buzhou[length].isred;
				}
				this.buzhou.splice(length,1);
				this.init();
			},
			fanHui(){
				uni.redirectTo({
					url: '../../pages/selectPage/selectPage',
					success: res => {console.log('返回主菜单！');},
					fail: (e) => {console.log(e)},
					complete: (e) => {console.log('complete:',e);}
				});
			},
			getStoneId(row ,col){
				for(var i=0;i<32;i++){
					if(this.qizi[i].row==row&&this.qizi[i].col==col&&!this.qizi[i].death){	
						return this.qizi[i].id;
						break;
					}
				}
				return -1;
			},
			// 一步人工智能
			// 1.看看有哪些步骤可以走
			// 2.试着走一下
			// 3.评估走的结果
			// 4.去最好的结果作为参考
			// 得到所有的可能走的步骤
			getAllPossibleMove(){
				console.log(this.bRedTurn);
				var min=0,max=16;   //得到不一样的所有步骤。
				if(this.bRedTurn){
					min=16;
					max=32;
				}
				var AllStep=[]
				for(var i=min;i<max;++i){
					if(this.qizi[i].death)continue;
					for(var row=0;row<=9;++row)
					{
						for(var col=0;col<=8;++col){
							var killid=this.getStoneId(row,col);
							if(killid<max&&killid>=min)continue;
							if(this.canMove(i, row, col, killid)){
								var beforMoveRow=this.qizi[i].row;
								var beforMoveCol=this.qizi[i].col;
								var isred=this.bRedTurn;
								var step ={
									killedId: killid,
									movedId:i,
									moveRow: beforMoveRow,
									moveCol: beforMoveCol,
									toRow: row,
									toCol: col,
									isred:isred,
								}
								AllStep.push(step);
							}
						}
					}
				}
				return AllStep;
			},
			
			computerMove(){
				var allPossibleMove=this.getAllPossibleMove();
				// 试着走一下
				// 评估走的结果
				var maxScore=-1000000;
				var bestStep;
				var length=allPossibleMove.length;
				for(var i=0;i<length;i++){
					var step=allPossibleMove[i];
					this.fakeMove(step);		
					var score=this.getMinScore(this.leave-1,maxScore);	
					this.unfakeMove(step);
					if(score>maxScore){
						maxScore=score;
						bestStep=step;
					}
				}
				return bestStep;
			},
			fakeMove(step){
				var killid=step.killedId
				if(killid!=-1)this.qizi[killid].death=true;
				this.moveStone(step.movedId,step.toRow,step.toCol);
			},
			unfakeMove(step){
				var killid=step.killedId
				if(killid!=-1)this.qizi[killid].death=false;
				this.moveStone(step.movedId,step.moveRow,step.moveCol);
			},
			calcScore(){
				var redTotalScore=0;
				var blackTotalScore=0;
				// 黑棋的总分-红旗的总分
				for(var i=0;i<16;i++){
					if(this.qizi[i].death)continue;
					blackTotalScore+=this.qizi[i].value;
				}
				for(var i=16;i<32;i++){
					if(this.qizi[i].death)continue;
					redTotalScore+=this.qizi[i].value;
				}
				return blackTotalScore-redTotalScore;
			},
			moveStone(moveid,row,col){
				this.qizi[moveid].row=row;
				this.qizi[moveid].col=col;
			},
			getMinScore(leave,curmaxScore){
				if(leave==0){
					return this.calcScore();
				}
				this.bRedTurn=!this.bRedTurn;
				var allPossibleMove=this.getAllPossibleMove();
				
				// 试着走一下
				// 评估走的结果
				var minScore=10000000;
				var length=allPossibleMove.length;
				// console.log("所有的步骤",allPossibleMove);
				for(var i=0;i<length;i++){
					var step=allPossibleMove[i];
					this.fakeMove(step);
					var score=this.getMaxScore(leave-1,minScore);
					this.unfakeMove(step);
					if(this.page=='AI4'){
						if(score<=curmaxScore){
							this.bRedTurn=!this.bRedTurn;
							allPossibleMove.splice(0,length);
							return score;
						}
					}
					if(score<minScore){
						minScore=score;
					}
				}
				this.bRedTurn=!this.bRedTurn;
				return minScore;
			},
			getMaxScore(leave,curminScore){
				if(leave==0){
					return this.calcScore();
				}
				this.bRedTurn=!this.bRedTurn;
				var allPossibleMove=this.getAllPossibleMove();
				
				// 试着走一下
				// 评估走的结果
				var maxScore=-10000000;
				var length=allPossibleMove.length;
				// console.log("所有的步骤",allPossibleMove);
				for(var i=0;i<length;i++){
					var step=allPossibleMove[i];
					this.fakeMove(step);
					var score=this.getMinScore(leave-1);
					this.unfakeMove(step);
					if(this.page=='AI4'){
						if(score>=curminScore){
							this.bRedTurn=!this.bRedTurn;
							allPossibleMove.splice(0,length);
							return score;
						}
					}

					if(score>maxScore){
						maxScore=score;
					}
				}
				this.bRedTurn=!this.bRedTurn;
				return maxScore;
			}
			
			
			
			
		},
		onLoad(e) {
			console.log(e);
			if(e.id=='AI'){
				this.isRoot=true;
			}
			this.page=e.sel;
			if(e.sel=='AI1'){
				this.leave=1;
			}
			if(e.sel=='AI2'){
				this.leave=2;
			}
			if(e.sel=='AI3'){
				this.leave=3;
			}
			
		},
		onShow() {},
		onReady() {
			this.init();
		},
	}
</script>
<style>
	/* 	#canvas{
		margin: 0 auto;
		padding: 0upx;
		height: 100%;
		width:100%;
		position: fixed;
		z-index: 2;
	} */
	.body {
		margin: 0;
		width: 100%;
		height: 100%;
		background-repeat: no-repeat;
		background: url(../../static/img/stype_1/bg.jpg);
		background-size: auto;
		position: fixed;
		flex-direction: column;
	}

	#qipan {
		margin: 0 auto;
		padding: 0upx;
		height: 100%;
		width: 100%;
		position: fixed;
		/* z-index: 1; */
	}

	#bg {
		margin-top: 0upx;
		margin-left: 0%;
		width: 100%;
		height: 100%;
	}

	#qizi {
		width: 80upx;
		height: 80upx;
		position: fixed;
		float: left;
		z-index: 5;
	}

	.bottom {
		width: 100%;
		height: 100upx;
		position: fixed;
		bottom: 0;
	}

	.button {
		width: 50%;
		height: 100%;
		position: relative;;
		display: inline;
		float:left ;
		margin-top: 100;
	}
</style>
