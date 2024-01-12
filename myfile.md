问题1：寄售、非寄售耗材的区分
答案：非寄售耗材：供应商把货物送到医院，医院验收之后，就算医院的资产，物权就会由供应商转到医院；
寄售耗材：供应商把货物送到医院之后，医院未消耗之前，都不算医院的资产；
问题2：耗材分为几种类型的耗材？
答案：耗材分为散货、一物一码、定数包耗材三种；
散货：价格比较低，无法向单个患者进收费；规格耗材字典“院内码管理”会设置为“无”；适用于送达核算；
一物一码：价格比较高，可以向单个患者进行收费；规格耗材字典“院内码管理”会设置为“系统生成”；适用于出库核算、计费核算；
定数包耗材：是由散货耗材按照一定的数量组成的包，会生成定数包条码；
备注：（1）一物一码耗材不可以设置为定数包耗材，（2）定数包耗材取用之后，不可以放回。适用于出库核算；
问题3：不同计费方式耗材，科室管理的程度？
答案：（1）送达核算，科室库不管该类耗材的实时库存；退货方式：取用退货、一键退货（耗材的寄售模式、形式发生变化）；
（1） 出库核算，科室管该理耗材的实时库存，退货方式：库存退货（有库存的情况下）、取用退货（已经取用了的耗材）、一键退货（耗材的寄售模式、形式发生变化）。
（2） 计费核算：科室管理该类耗材的实时库存；特点：可以获取该类耗材的取用点，并且是最小单位的耗材可以向患者收费，该类耗材取用到his未计费之前都可以放回；

问题4：核算方式的定义
答案：系统目前有3种核算方式（送达核算、出库核算、计费核算），核算方式是医院跟科室之间成本核算的方式；
送达核算：物流中心配送到科室，科室接收之后，立即生成科室成本；
出库核算：物流中心配送到科室，科室取用，生成科室正向成本；科室放回耗材，生成负向成本；
（3） 计费核算：物流中心配送到科室，取用、放回耗材都不会产生成本，只有his完成收费时，才会产生科室成本；his计费完成的耗材如何进行退货：需要再his系统里面完成一个冲账的操作，然后spd系统收到的是冲账之后，是可以在spd系统内把这种耗材退掉的；
问题5：实时库存分为几种类型的库存？
答案：存储区（可用量、占用量）、不可用库存（隔离区、不合格区、退货区）；
中心仓占用量：
（1） 拣货-出库单（手持）；
（2） 未完成状态（未接收、部分接收）的出库单（未出库的出库单、已出库未接收的出库单）；
（3） 未上架状态打包拣货单（未上架之前，会产生对应散货的占用量，上架之后，散货库存消失，会转换成相应的定数包库存）；
（4） 未上架状态拆包单（未上架状态的拆包单，产生的是定数包的占用量，拆包之后，定数包实时库存减少，增加对应散货的库存）；
（5） 未确认状态的耗材移动单；
（6） 未入库的科室退库单（未接收状态的退库单，占用量是在科室库，当中心仓接收之后，科室库的库存减少，中心仓增加相应的库存）；其中只有退库类型为库存退货的，才会产生科室库的占用库存，其他类型的退库不会产生科室库的占用库存；
（7） 未出库的退货单（未出库状态的退货单，产生中心仓的占用量，出库之后，实时库存减少）、耗材移动（产生对应耗材的占用量，确认移动之后，才会把占用量释放）、
（8） 未入库状态的耗材调拨单；
科室库占用量：
（1）未入库状态的退库单（库存退库）；
问题6：怎么停用一个规格耗材字典？
答案：停用一种规格耗材要满足以下条件：
（1）该耗材对应的定数包都是停用状态；
（2）该耗材没有实时库存：包括可用量（中心仓、科室库）、占用量（中心仓、科室库）；
（3） 没有以下未关闭状态的单据：
（a）未关闭的采购订单；
（b）未入库验收的发运单；
（c）未关闭的请领单；
（d）未关闭的拣货单；
问题7：怎么停用一个定数包字典？
答案：满足以下条件：
（1）该定数包没有实时库存（包括中心仓、科室库）；
（2）没有以下未关闭状态的单据：
（a）未关闭的采购订单；
（b）未入库验收的发运单；
（c）未关闭的请领单；
（d）未关闭的拣货单；
问题8：科室智能补货的逻辑
答案：智能补货公式（补货量）=智能补货 = 科室库的最高库存 - 科室现有库存 - 已经申请待汇总的计划量 - 科室欠货量；
常见问题，耗材设置为主动补货了，实时库存也低于科室库房最高库存，但是进行智能补货时，无法给该耗材进行主动补货；
答案：这时要去查看该耗材是否有欠货、申请未汇总、配送未接收等；
问题9：科室欠货量概念及科室关闭欠货的条件？
答案：护士下完计划之后，科室欠货量不会立即发生变化，只有计划被汇总之后，欠货量才会发生变化；中心仓一旦配送出库之后，科室欠货量就会发生变化；科室全部接收，科室欠货量不发生变化，科室部分接收并关闭配送单情况下，科室欠货量会发生变化。
来源：2个；（1）汇总的需求计划；（2）新建的请领单；
举例说明：（1）护士A在科室A新建计划耗材a10个，这时中心仓对科室时没有欠货量；（2）物流中心的工作人员把护士A的这个需求计划汇总，这时物流中心对科室A的欠货量为10；（3）物流中心拣货配送给科室5个，这时，物流中心对科室A的欠货量为5，（4）科室A接收了3个耗材，拒收了2个，这时物流中心对科室A的欠货量变为7，已接收量为3个。
关闭欠货的条件：无条件，只要有欠货就可以进行关闭，关闭之后，系统自动完成请领单、拣货单、配送单中该耗材的处理；
（1） 关闭的耗材欠货只存在于请领单中，该耗材被自动关闭，欠货量变为0，不需要再给科室进行拣货配送；
（2） 关闭的耗材存在于请领单及拣货单中：对应的请领单及拣货单中该耗材被关闭，请领单中该耗材的欠货量为0，拣货单中该耗材被释放出来，由占用库存转变为可用库存；
（3） 关闭的耗材存在于请领单、拣货单、配送单中：对应的请领单、拣货单、配送单中该耗材被关闭，其中请领单中该耗材的欠货量变为0，拣货单中该耗材被关闭，配送单中该耗材也被自动关闭，科室收货时，此耗材已经无法收货，由占用库存转变为可用库存；
问题10：如何设置医院科室新建计划调用的库房耗材目录及不同设置下面对应耗材目录？
答案：【系统设置】-【自定义配置】-【需求计划调用库房耗材目录设置】设置需求计划调用耗材目录；
若设置为一级库房耗材目录，科室在下计划时，可以调用该分院下面所有的一级库；
若设置为科室库房耗材目录，科室在下计划时，只可以调用自己所在科室库房的耗材目录；
问题11：如何给科室进行主动补货？
答案：（1）在科室库房耗材目录里面设置“是否主动补货”为“是”（只有出库核算、计费核算的耗材才可以进行主动补货，送达核算的耗材不可以进行主动补货）；
（2） 设置该耗材的安全库存、最高库存（根据科室的实际使用情况来设计）；
（3） 主动补货分为预警补货（只有主动补货，且该耗材在科室的实时库存低于安全库存，才会进行补货）、全部补货（所有主动补货的耗材都会进主动补货）；
问题12：科室库房是怎么设置不同的改造方式的？
答案：科室库房有以下几种改造方式：不做任何改造、触屏终端改造、智能柜改造、RFID智能柜改造、RFID扫描平台改造；
（1）若科室库房不做任何的改造，不用做任何的设置；
（2）若是触屏终端改造，则需要按照以下路径绑定库房的终端Mac地址，一个科室库房可以绑定多个mac地址（即一个科室可以安装多台触屏终端）；多个科室可以绑定一个mac地址（即多个科室可以绑定同一台触屏终端）
（1） 普通智能柜改造，则需要启用智能柜，并且选择智能柜类型为“普通柜”；一个科室库房可以绑定多个mac地址（即一个科室可以安装多组普通柜）；多个科室可以绑定一个mac地址（即多个科室可以绑定同一组普通柜）
（2） 若是RFID智能柜改造，则需要启用智能柜，并且选择智能柜类型为“RFID柜或RFID扫描平台”；一个科室库房可以绑定多个mac地址（即一个科室可以安装多组RFID柜）；多个科室可以绑定一个mac地址（即多个科室可以绑定同一组RFID柜）
（3） 若是RFID扫描平台改造，则需要启用智能柜，并且选择智能柜类型为“RFID柜或RFID扫描平台”；一个科室库房可以绑定多个mac地址（即一个科室可以安装多个RFID扫描平台）；多个科室可以绑定一个mac地址（即多个科室可以绑定同一个RFID扫描平台）

问题13：目前系统中存在的单据中，哪些是可以支持拆单的，及拆单的原则是？
答案：目前系统支持6种单据的拆单，分别是科室需求计划单、采购计划单、采购订单、配送出库单、供应商结账单、科室结账单；
（1）需求计划拆单院长：按照耗材高低值、耗材审核等级、耗材所属中心库房；
如何设置？通过【系统设置】-【自定义设置】-【需求计划拆单设置】进行配置，可以配置拆单，也可以配置不拆单；
（2）采购计划的拆单原则：按照耗材高低值、耗材所属供应商进行拆分；
如何设置？通过【系统设置】-【自定义设置】-【采购计划拆单设置】进行配置，可以配置拆单，也可以配置不拆单；
（3）采购订单的拆单原则：按照耗材管理方式、耗材是否省平台采购进行拆单
如何设置？通过【系统设置】-【自定义设置】-【采购订单拆单设置】进行配置，可以配置拆单，也可以配置不拆单；
（4） 配送出库单的拆单原则：按照单据中的耗材种类、耗材所属分类、耗材的管理方式、耗材的寄售模式、耗材的采购方式等原则进行拆单；
如何设置？通过【系统设置】-【自定义设置】-【配送出库单拆单设置】进行配置，可以配置拆单，也可以配置不拆单；
（5） 供应商结账单拆单原则：按照耗材所属分类、耗材是否省平台采购、耗材的核算方式进行拆单；
如何设置？通过【系统设置】-【自定义设置】-【供应商结账单拆单设置】进行配置，可以配置拆单，也可以配置不拆单；

（6） 科室结账单拆单原则：按照耗材所属分类、核算方式进行拆单；
如何设置？通过【系统设置】-【自定义设置】-【结账单拆单设置】进行配置，可以配置拆单，也可以配置不拆单；
问题14：供货清单里面的供应商更换可以完成哪些功能？
答案：可以完成的功能有：
1、不带着原供应商的实时库存进行供应商更换，其中耗材的单价、寄售模式不修改：把耗材A由供应商A更换为供应商B：
可以修改的前提条件：耗材A的耗材状态是正常的，耗材A在供应商A的清单状态是正常的；
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）以相同的单价、寄售模式更换或者新建耗材A在供应商B 的供货清单；
A）若系统中原来存在耗材A在供应商B的供货清单，且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
2、不带着原供应商的实时库存进行供应商更换，其中耗材的单价修改、寄售模式不修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以新的单价、供应商A对应的供货清单对应的寄售模式启用或者新建；
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
3、不带着原供应商的实时库存进行供应商更换，其中耗材的单价不修改、寄售模式修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以供应商A对应的供货清单的单价、修改的寄售模式启用或者新建；
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
4、不带着原供应商的实时库存进行供应商更换，其中耗材的单价修改、寄售模式修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单给停用；
2）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
3）供应商B对应的供货清单以新单价、修改的寄售模式启用或者新建；
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件可以修改：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
5、带着原供应商的实时库存进行供应商更换，其中耗材的单价、寄售模式不修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以供应商A对应的供货清单的单价、寄售模式启用或者新建；
3）把科室库的所有实时库存退货到中心仓，并完成自动中心仓（科室库库存退货）；
4）把中心仓所有的库存产生退货单，并且自动完成退货；（生成A供应商的退货单）；
5）以供应商B入库所有的耗材，并完成自动审核验收上架（生成供应商B的审核通过状态的入库验收单）同时生成所有的一物一码耗材的条码（条码是可以复用的）；
6）所有的定数包条码重新生成；（在原来的定数包拣货单的基础上去修改）；
7）把科室实时库存再以新的供应商配送到对应的科室（生成对应的配送单，并完成自动接收）；备注：若医院所用的条码中有供应商字段，需要重新打印的条码，把条码配送到科室，重新贴到耗材上，需要把原来的条码覆盖；若医院所用的条码没有供应商字段，不需要重新打印条码；
8）生成供应商更换记录；
供应商可以更换的条件：
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
B）供应商A可更换到供应商B的条件：
a）科室库没有待接收的配送单，若有处于待接收的配送单，需要关闭或者完成接收；
b）中心仓没有待审核的配送单，若有需要审核通过或者不通过待审核的配送单，若审核通过，需要再把审核通过的配送单给手动关闭；若审核不通过，需要把该配送单对应的拣货单手动关闭；
c）中心仓没有待出库的拣货单，若有，需要手动关闭拣货单；
d）中心仓没有待确认的移动单，若有，需要手动确认移动；
e）中心仓没有待上架的打包上架，须有，需要手动确定或者修改；
f）中心仓没有待上架的拆包单，若有，需要手动确定；
g）没有待入中心仓的科室退库单，若有需要手动关闭；
h）没有待出库的退货单（中心仓有待出库的退给供应商的退货单），若有需要手动关闭；
6、带着原供应商的实时库存进行供应商更换，其中耗材的单价变化、寄售模式不修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以新的单价、供应商A对应寄售模式启用或者新建；
3）把科室库的所有实时库存退货到中心仓，并完成自动中心仓（科室库库存退货）；
4）把中心仓所有的库存产生退货单，并且自动完成退货；（生成A供应商的退货单）；
5）以供应商B以新的单价入库所有的耗材，并完成自动审核验收上架（生成供应商B的审核通过状态的入库验收单）同时生成所有的一物一码耗材的条码（条码是可以复用的）；
6）所有的定数包条码重新生成；（在原来的定数包拣货单的基础上去修改）；
7）把科室实时库存再以新的供应商配送到对应的科室（生成对应的配送单，并完成自动接收）；备注：若医院所用的条码中有供应商字段，需要重新打印的条码，把条码配送到科室，重新贴到耗材上，需要把原来的条码覆盖；若医院所用的条码没有供应商字段，不需要重新打印条码；
8）生成供应商更换记录；
供应商可以更换的条件：
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
B）供应商A可更换到供应商B的条件：
a）科室库没有待接收的配送单，若有处于待接收的配送单，需要关闭或者完成接收；
b）中心仓没有待审核的配送单，若有需要审核通过或者不通过待审核的配送单，若审核通过，需要再把审核通过的配送单给手动关闭；若审核不通过，需要把该配送单对应的拣货单手动关闭；
c）中心仓没有待出库的拣货单，若有，需要手动关闭拣货单；
d）中心仓没有待确认的移动单，若有，需要手动确认移动；
e）中心仓没有待上架的打包上架，须有，需要手动确定或者修改；
f）中心仓没有待上架的拆包单，若有，需要手动确定；
g）没有待入中心仓的科室退库单，若有需要手动关闭；
h）没有待出库的退货单（中心仓有待出库的退给供应商的退货单），若有需要手动关闭；
7、带着原供应商的实时库存进行供应商更换，其中耗材的单价不变、寄售模式修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以供应商A对应的供货清单的单价、修改的寄售模式启用或者新建；
3）把科室库的所有实时库存退货到中心仓，并完成自动中心仓（科室库库存退货）；
4）把中心仓所有的库存产生退货单，并且自动完成退货；（生成A供应商的退货单）；
5）以供应商B新的寄售模式入库所有的耗材，并完成自动审核验收上架（生成供应商B的审核通过状态的入库验收单）同时生成所有的一物一码耗材的条码（条码是可以复用的）；
6）所有的定数包条码重新生成；（在原来的定数包拣货单的基础上去修改）；
7）把科室实时库存再以新的供应商配送到对应的科室（生成对应的配送单，并完成自动接收）；备注：若医院所用的条码中有供应商字段，需要重新打印的条码，把条码配送到科室，重新贴到耗材上，需要把原来的条码覆盖；若医院所用的条码没有供应商字段，不需要重新打印条码；
8）生成供应商更换记录；
供应商可以更换的条件：
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
B）供应商A可更换到供应商B的条件：
a）科室库没有待接收的配送单，若有处于待接收的配送单，需要关闭或者完成接收；
b）中心仓没有待审核的配送单，若有需要审核通过或者不通过待审核的配送单，若审核通过，需要再把审核通过的配送单给手动关闭；若审核不通过，需要把该配送单对应的拣货单手动关闭；
c）中心仓没有待出库的拣货单，若有，需要手动关闭拣货单；
d）中心仓没有待确认的移动单，若有，需要手动确认移动；
e）中心仓没有待上架的打包上架，须有，需要手动确定或者修改；
f）中心仓没有待上架的拆包单，若有，需要手动确定；
g）没有待入中心仓的科室退库单，若有需要手动关闭；
h）没有待出库的退货单（中心仓有待出库的退给供应商的退货单），若有需要手动关闭；
8、带着原供应商的实时库存进行供应商更换，其中耗材的单价变化、寄售模式修改：把耗材A由供应商A更换为供应商B：
把耗材A的供应商由供应商A改为供应商B之后，会发生以下变化：
1）供应商A对应的供货清单以原来的修改之前的单价、寄售模式停用；
2）供应商B对应的供货清单以新单价、修改的寄售模式启用或者新建；
3）把科室库的所有实时库存退货到中心仓，并完成自动中心仓（科室库库存退货）；
4）把中心仓所有的库存产生退货单，并且自动完成退货；（生成A供应商的退货单）；
5）以供应商B新单价、新的寄售模式入库所有的耗材，并完成自动审核验收上架（生成供应商B的审核通过状态的入库验收单）同时生成所有的一物一码耗材的条码（条码是可以复用的）；
6）所有的定数包条码重新生成；（在原来的定数包拣货单的基础上去修改）；
7）把科室实时库存再以新的供应商配送到对应的科室（生成对应的配送单，并完成自动接收）；备注：若医院所用的条码中有供应商字段，需要重新打印的条码，把条码配送到科室，重新贴到耗材上，需要把原来的条码覆盖；若医院所用的条码没有供应商字段，不需要重新打印条码；
8）生成供应商更换记录；
供应商可以更换的条件：
A）若系统中原来存在耗材A在供应商B的供货清单（或者耗材A不存在供应商B的供货清单），且满足以下条件：
a）清单状态是正常（停用）、寄售模式相同；
b）清单状态是正常（停用）、寄售模式不同，但是耗材A在供应商B没有实时库存；
c）若耗材A在供应商A、B的寄售模式不同的情况下，更换成功之后，耗材A原来在供应B下面的取用退库只能采用一键退货；
B）供应商A可更换到供应商B的条件：
a）科室库没有待接收的配送单，若有处于待接收的配送单，需要关闭或者完成接收；
b）中心仓没有待审核的配送单，若有需要审核通过或者不通过待审核的配送单，若审核通过，需要再把审核通过的配送单给手动关闭；若审核不通过，需要把该配送单对应的拣货单手动关闭；
c）中心仓没有待出库的拣货单，若有，需要手动关闭拣货单；
d）中心仓没有待确认的移动单，若有，需要手动确认移动；
e）中心仓没有待上架的打包上架，须有，需要手动确定或者修改；
f）中心仓没有待上架的拆包单，若有，需要手动确定；
g）没有待入中心仓的科室退库单，若有需要手动关闭；
h）没有待出库的退货单（中心仓有待出库的退给供应商的退货单），若有需要手动关闭；
备注：带着库存进行供应商更户的时候，没有补发运单（如果要补发运单的话，要补订单，采购计划等一系列的单据），所以如果医院要求入库必须有发运单的，请慎用此功能。

问题14：供应商更换之后，条码是可以复用的吗？线下应该需要注意哪些？
答案：条码是可以复用的，但是如果有的医院用的条码上有供应商字段的话，需要把条码给重新打印，重新贴到原来的耗材上；
贴条码时，需要注意应该把原来的条码撕掉或者用新的条码把旧的条码完全覆盖；

问题15：如何停用一个中心仓？停用中心仓之后，可以继续哪些操作？不可以哪些操作？
答案：中心仓的停用、启用是没有任何条件；
停用之后可以继续的操作：
1） 科室可向该中心仓申请耗材；
2） 中心仓可以汇总科室需求计划；
3） 新建请领；
4） 可以拣货、出库，
5） 接受科室退库；
6） 退货给供应商；
7） 入库验收停用之前的发运单（订单）；
停用之后不可以继续的操作：
1） 新建采购；
2） 一步入库；
3） 打包、拆包；
4） 耗材移动；
5） 一键出库；（若想把耗材直接出给科室，请先给科室创建请领计划）；
6） 直入直出；
问题16：债权转让的相关问题？
（1） 哪些供应商可以进行债权转让？
答案：供应商有耗材进行过供应商更户，就是供货清单里面的供应商更换里面的更换类型为“供应商更户”的供应商才可以进行供应商债权转让；
（2） 债权转让是怎么处理的？
答案：在债权转让时，针对耗材级别的债权转让；举例说明供应商A的耗材A、B更换给供应商B，供应商A的耗材D、E更换给供应商C；供应商A的耗材C没有进行过更户或者转配送；在给供应商A创建债权转让时，给供应商A创建债权转让时，可以选择的债权转让的供应商有供应商B，供应商C；创建供应商A跟供应商B的债权转让，对应的转让的耗材是A、B；创建供应商A跟供应商C的债权转让时，对应的转让的耗材是C、D；
（3） 创建了债权转让之后，在哪些地方可以用到？
答案：创建了债权转让的供应商，在创建付款计划时，旧供应商的成本直接转给新的供应商；
（4） 债权转让里面的耗材数量是怎么计算的？
答案：债权转让里面的耗材数量是实时的，只要2家供应商存在正常状态的债权转让协议，2家供应商之间签订的类型为供应商转换的，就可以自动添加；
（5） 债权转让之后，发票是怎么处理的？
答案：只要2家供应商存在正常状态的债权转让关系，那么旧供应商的需要开具发票的明细都在新供应商的账号显示，显示为转入；

问题17：供应商更换、债权转让、发票、付款计划之间的关系？
答案：供应商更换的类型分为：转配送、供应商更户2种不同的类型；分别适用以下不同的场景；
下面以国药（1）为原供应商；国药（2）、华润为新供应商举例说明；其中国药（1）、国药（2）的幕后老板是一个；
转配送适用于以下场景：
（1） 国药（1）无法继续给医院某种或者某些种耗材，但是医院还要继续使用此种耗材时，医院决定把配送权转给华润；
（2） 医院因为国药（1）供货不及时等原因（某种或者某些），医院决定停用国药的供货，但是医院还要继续使用此种耗材时，把转给华润；
总结的来说：耗材的转配送，2家供应商之间的债权关系是各自负责各自的账务；
供应商更户适用于以下场景：
（1） 国药（1）给医院配送的耗材，如果再继续以国药（1）进行配送的话，就会产生更高的税率，为了合理的避税，供应商要求医院配合把供应商（1）供的某一种或者某些或者全部耗材都更户给国药（2）；
（2） 国药（1）因运营的关系，公司永久停止运营，无法开具发票等，公司要求医院把供应商（1）供的耗材更户给国药（2）；
总结的来说：进行更户的供应商的幕后老板是一家，债权关系可以转让，也可以不转让；
债权转让的意义：
供应商更户之后，2个供应商之间的债务关系，没有必然的关系，既可以各自承担各自的债务，也可以把原供应商的债务转让给新的供应商，到底怎么处理2家供应商之间的债务，需求在系统中签订债权转让协议来确定；
供应商债权转让：
（1） 新旧供应商之间存在更户的供货清单；
（2） 债权转让是在供应商、耗材2个维度的；举例说明：供应商A最开始给医院供100种耗材，后来转配送给供应商B 10种耗材，更户给供应商C 20种，更户给供应商D 30种，则具体的处理方案：
供应商A、B不可以签订债权转让协议；
供应商A、C可以签订债权转让协议，但是可以进行债权转让的耗材种类为20种；
供应商A、D可以签订债权转让协议，但是可以进行债权转让的耗材种类为30种；
债权转让协议签订之后：新旧供应商之间的发票（成本）是怎么处理的？
答案：即使供应商之间签订了债权转让协议，也是哪家供应商产生的成本算在谁的身上，发票可以是不同的供应商进行开具；
在spd系统内进行发票登记时，还是要谁的成本登记到哪家供应商，但是可以用开票商这一个字段来区分发票到底是谁来开具的（钱到底付给谁）；
债权转让协议签订之后，创建付款计划是如何处理的？
答案：在创建付款计划时，需要判断2家供应商之间的债权转让协议状态是否正常，若是正常则在创建付款计划时，原供应商的应付款全部转让到B供应商；若2家供应商之间的债权转让协议状态是停用，则创建付款计划时，各自承担各自的应付款；
原供应商的负向成本怎么处理？
为了保证spd系统的出入库数据是平的，原供应商的负向成本仍然是原供应商的，只是在开具发票的时候，可以用开票商来解决原供应商开具不出发票的问题？
供应商怎么知道如何开具原供应商的负向发票？
答案：目前供应商是通过云平台的发票查看来进行查看数据开具发票的，如果发票明细里面是标有这2个字段是否债权转让“是”，转让类型“转入”，这是需要新供应商帮着旧供应商开具的负票；
问题18：规格耗材字典每一个字段的含义？
答案：
1） 耗材编码：系统生成或者手动输入，这个是由自定义配置来确定的；编码规则一般上线的时候，实施配置系统生成编码规则；如果配置了多种耗材编码生成规则，则生成耗材的时候，需要选择耗材编码的前缀；
2） 耗材名称：输入项；必填项；
3） 规格型号：输入项；必填项；
4） 单位：选择项；选项内容来源于【基础数据】-【字典管理】类型为“单位”的字典；必选项；
5） 生产厂家：选择项；选项内容来源于【基础数据】-【供应厂商】字段“是否生产厂家”为是的厂商；必选项；
6） 品牌：选择项；选项内容来源于【基础数据】-【字典管理】类型为“品牌”的字典；必选项；
7） 耗材分类：选择项；选项内容来源于【基础数据】-【耗材分类】类型为“业务分类”的耗材分类；必选项；
8） 小包装规格：输入项；非必填项；
9） 小包装规格系数：输入项；非必填项；
10） 中包装规格：输入项；非必填项；
11） 中包装规格系数：输入项；非必填项；
12） 大包装规格：输入项；非必填项；
13） 大包装规格系数：输入项；非必填项；
14） 医院编码：输入项；非必填项；
15） 省平台编码：输入项；非必填项；
16） 药交ID：输入项；非必填项；
17） 商品常用名：输入项；非必填项；
18） 单位重量：输入项；非必填项；
19） 单位体积：输入项；非必填项；
20） 厂商码必填：选择项；必选项；选项内容：是、否（默认选项）；
A） 若字段被赋值“是”，则代表耗材是“厂商码耗材”，则每一个最小使用单位的耗材都有自己的厂商码，耗材出厂的时候，就有自己唯一的身份ID；
B） 若字段被赋值“否”，则代表耗材是非厂商码耗材；
21） 院内码管理：选择项；必选项；选项内容跟字段厂商码字段值相关联；
a） 若厂商码必填赋值为“否”，则院内码管理选项内容：“系统生成”、“无”（默认选项）；b）若厂商码必填赋值为“是”，则院内码管理选项内容：系统生成（默认选项）、跟厂商码一致；
A） 耗材是非厂商码，且院内码管理是“无”时，代表这种耗材是散货；
B） 耗材是非厂商码耗材，且院内管理是“是”时，代表这种耗材是一物一码；
C） 耗材是厂商码耗材，不管院内管理是何值，代表这种耗材是一物一码；
22） 是否灭菌：选择项，必选项；选项内容：是、否（默认选项）；耗材一旦创建，此字段是不可以修改的；
A）是否灭菌是耗材本身的属性，此值不可以修改；
23） 是否消毒：选择项，必选项；选项内容：是、否（默认选项）；
24） 是否收费：选择项，必选项；选项内容：是、否（默认选项）；
A）是否收费代表这种耗材是可以单独跟患者收费；
25） 是否招标：选择项，必选项；选项内容：是、否（默认选项）；
26） 请领基数：输入项，只支持整数；
27） 采购基数：输入项，只支持整数；
28） 显示排序：输入项；只支持整数；
29） 状态：选择项，必选项；选项内容：正常（默认选项）、停用；
30） 耗材类别：选择项，必选项；选项内容：国产（默认选项）、进口、合资；
A）不同类型的耗材需要认证的资料不同；
31） 效期管理：选择项，必选项；选项内容：是、否（默认选项）；耗材一旦创建，此字段是不可以修改的；
A） 效期管理是耗材本身的属性，若耗材的有效期是固定的，则效期管理设置为“是”，耗材有生产日期、失效日期；例如灭菌纱布等；
B） 若耗材的有效期是不固定的，则效期管理为“否”，耗材只有生产日期，没有失效日期；如不锈钢盆等；
32） 注册账号：输入项，非必填项；
33） 注册证名称：输入项，非必填项；
34） 是否平台采购：选择项，必选项；选项内容：是、否（默认选项）；
35） 是否停止采购：选择项，必选项；选项内容：是、否（默认选项）；此字段的含义代表的是，医院是否可以采购此耗材，一旦耗材被维护成“是”，不可以再向供应商采购耗材；
36） 默认核算方式：选择项；选项内容：出库核算（默认选项）、送达核算、计费核算；
A）默认核算方式用于库房耗材目录维护，当耗材添加到某一库房时，核算方式默认取值于规格耗材字典里面的“默认核算方式”；
37） 备注：输入项，非必填项；
备注：耗材名称+规格型号+单位+生产厂商+是否灭菌这五个字段确定一个规格耗材，排除空格。
问题19：供货清单每一个字段的含义？
答案：供货清单，是医院跟供应商之间的桥梁，医院跟供应商以什么样的价格、什么样的寄售模式采购哪些耗材，及采购的合同时长是多久都是通过供货清单来维护的，所以理解供货清单的的每一个字段含义至关重要。且规格耗材分为父类耗材子类耗材，不可以单独给父类耗材创建供货清单，只有父类耗材有了供货清单，子类耗材才可以创建供货清单；
1） 供应商：医院采购哪一家供应商的耗材，就需要把对应的供应商选择添加进来；
2） 耗材编码：医院向哪一家供应商采购哪一种耗材，就需要把对应的耗材添加进来；
3） 省平台编码：这些是耗材本身自带信息；
4） 医院编码：这些是耗材本身自带信息；
5） 耗材名称：这些是耗材本身自带信息；
6） 规格型号：这些是耗材本身自带信息；
7） 单位：这些是耗材本身自带信息；
8） 包装规格：这些是耗材本身自带信息；
9） 品牌：这些是耗材本身自带信息；
10） 生产厂家：这些是耗材本身自带信息；
11） 单价：耗材的采购价格；支持单价为0的输入，主要是一些企业捐赠的耗材；