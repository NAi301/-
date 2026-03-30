# <!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>大学生付费实习乱象调查问卷</title>
    <!-- 引入QRCode生成库 -->
    <script src="https://cdn.jsdelivr.net/npm/qrcodejs2-fix@0.0.1/qrcode.min.js"></script>
    <!-- 可选字体与样式 -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f0f4f8;
            font-family: 'Inter', sans-serif;
            padding: 30px 20px;
            color: #1e2a3e;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 28px;
            box-shadow: 0 20px 35px -12px rgba(0,0,0,0.1);
            overflow: hidden;
            padding: 30px 28px 48px;
        }

        h1 {
            font-size: 1.9rem;
            font-weight: 700;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 8px;
        }

        .sub {
            color: #4a627a;
            border-left: 4px solid #2a7f6e;
            padding-left: 16px;
            margin: 16px 0 28px 0;
            font-size: 0.95rem;
            background: #f8fafc;
            border-radius: 12px;
            padding: 12px 16px;
        }

        .qr-section {
            background: #f8fafc;
            border-radius: 20px;
            padding: 18px 20px;
            margin-bottom: 32px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 20px;
            border: 1px solid #e2edf2;
        }

        .qr-text {
            flex: 1;
        }

        .qr-text p {
            font-size: 0.9rem;
            color: #2c3e50;
            margin-bottom: 6px;
        }

        .qr-code {
            background: white;
            padding: 10px;
            border-radius: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            display: inline-block;
        }

        #qrcode {
            width: 100px;
            height: 100px;
        }

        .section {
            margin-bottom: 36px;
            border-bottom: 1px solid #e9eef3;
            padding-bottom: 24px;
        }

        .section-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #0f2b3d;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .section-title span {
            background: #2a7f6e20;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.8rem;
            font-weight: 500;
            color: #1f6e5c;
        }

        .question {
            margin-bottom: 28px;
        }

        .q-title {
            font-weight: 600;
            margin-bottom: 12px;
            font-size: 1rem;
            color: #1e2f41;
        }

        .options {
            display: flex;
            flex-wrap: wrap;
            gap: 16px 28px;
            align-items: center;
        }

        .radio-option, .checkbox-option {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        input[type="radio"], input[type="checkbox"] {
            width: 18px;
            height: 18px;
            accent-color: #2a7f6e;
            cursor: pointer;
        }

        .inline-group {
            display: flex;
            flex-wrap: wrap;
            gap: 12px 24px;
            margin-top: 6px;
        }

        .other-input {
            margin-left: 28px;
            margin-top: 8px;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }

        .other-input input {
            padding: 6px 12px;
            border-radius: 30px;
            border: 1px solid #cbd5e1;
            font-size: 0.85rem;
            width: 200px;
        }

        hr {
            margin: 20px 0;
            border: none;
            border-top: 1px dashed #dce5ec;
        }

        button {
            background: #1f6e5c;
            color: white;
            border: none;
            padding: 14px 28px;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 48px;
            cursor: pointer;
            transition: 0.2s;
            margin-top: 18px;
            margin-right: 16px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        }

        button:hover {
            background: #0e5546;
            transform: translateY(-1px);
        }

        .btn-secondary {
            background: #e2e8f0;
            color: #1f2f3e;
            box-shadow: none;
        }

        .btn-secondary:hover {
            background: #cbd5e1;
        }

        .footer-note {
            font-size: 0.75rem;
            text-align: center;
            margin-top: 32px;
            color: #6c86a3;
            border-top: 1px solid #e2edf2;
            padding-top: 20px;
        }

        @media (max-width: 640px) {
            .container {
                padding: 20px 16px;
            }
            .options {
                gap: 12px;
                flex-direction: column;
                align-items: flex-start;
            }
            .qr-section {
                flex-direction: column;
                align-items: flex-start;
            }
        }
    </style>
</head>
<body>
<div class="container">
    <h1>📊 大学生付费实习乱象调查问卷</h1>
    <div class="sub">
        亲爱的同学，你好！本次问卷旨在调研大学生付费实习乱象的现状、成因及治理诉求，为整治付费实习灰色产业、维护就业公平提供实证依据。<br>
        问卷采用匿名形式，所有数据仅用于学术研究，严格保密个人信息，感谢你的支持与配合！
    </div>

    <!-- 二维码分享区：动态生成当前页面链接的二维码 -->
    <div class="qr-section">
        <div class="qr-text">
            <p>📱 扫描二维码填写问卷</p>
            <p style="font-size:0.8rem; color:#4a627a;">将此页面部署至服务器后，二维码自动指向当前问卷链接，方便分享给同学填写。</p>
        </div>
        <div class="qr-code" id="qrcode"></div>
    </div>

    <form id="surveyForm">
        <!-- 一、个人基本信息 -->
        <div class="section">
            <div class="section-title"><span>一</span> 个人基本信息</div>
            <div class="question"><div class="q-title">1. 你的性别：</div><div class="options"><label class="radio-option"><input type="radio" name="gender" value="男"> 男</label><label class="radio-option"><input type="radio" name="gender" value="女"> 女</label></div></div>
            <div class="question"><div class="q-title">2. 你所在的年级：</div><div class="options"><label class="radio-option"><input type="radio" name="grade" value="大一"> 大一</label><label class="radio-option"><input type="radio" name="grade" value="大二"> 大二</label><label class="radio-option"><input type="radio" name="grade" value="大三"> 大三</label><label class="radio-option"><input type="radio" name="grade" value="大四"> 大四</label><label class="radio-option"><input type="radio" name="grade" value="研究生"> 研究生</label></div></div>
            <div class="question"><div class="q-title">3. 你所在的院校层次：</div><div class="options"><label class="radio-option"><input type="radio" name="univ_level" value="985/211/双一流院校"> 985/211/双一流院校</label><label class="radio-option"><input type="radio" name="univ_level" value="普通本科院校"> 普通本科院校</label><label class="radio-option"><input type="radio" name="univ_level" value="民办本科院校"> 民办本科院校</label><label class="radio-option"><input type="radio" name="univ_level" value="高职高专院校"> 高职高专院校</label></div></div>
            <div class="question"><div class="q-title">4. 你所学专业属于：</div><div class="options"><label class="radio-option"><input type="radio" name="major" value="经济学/金融学类"> 经济学/金融学类</label><label class="radio-option"><input type="radio" name="major" value="文法类"> 文法类</label><label class="radio-option"><input type="radio" name="major" value="理工类"> 理工类</label><label class="radio-option"><input type="radio" name="major" value="医药类"> 医药类</label><label class="radio-option"><input type="radio" name="major" value="艺术类"> 艺术类</label><label class="radio-option"><input type="radio" name="major" value="其他"> 其他</label></div></div>
            <div class="question"><div class="q-title">5. 毕业后你的规划是：</div><div class="options"><label class="radio-option"><input type="radio" name="plan" value="直接就业"> 直接就业</label><label class="radio-option"><input type="radio" name="plan" value="考研深造"> 考研深造</label><label class="radio-option"><input type="radio" name="plan" value="考公/考编"> 考公/考编</label><label class="radio-option"><input type="radio" name="plan" value="出国留学"> 出国留学</label><label class="radio-option"><input type="radio" name="plan" value="暂未确定"> 暂未确定</label></div></div>
            <div class="question"><div class="q-title">6. 你的家庭经济条件：</div><div class="options"><label class="radio-option"><input type="radio" name="family_eco" value="较为优越"> 较为优越</label><label class="radio-option"><input type="radio" name="family_eco" value="中等水平"> 中等水平</label><label class="radio-option"><input type="radio" name="family_eco" value="一般"> 一般</label><label class="radio-option"><input type="radio" name="family_eco" value="较为困难"> 较为困难</label></div></div>
        </div>

        <!-- 二、实习经历与求职认知 -->
        <div class="section">
            <div class="section-title"><span>二</span> 实习经历与求职认知</div>
            <div class="question"><div class="q-title">1. 你目前是否有过实习经历：</div><div class="options"><label class="radio-option"><input type="radio" name="intern_exp" value="有，1段及以上"> 有，1段及以上</label><label class="radio-option"><input type="radio" name="intern_exp" value="暂无实习经历"> 暂无实习经历</label></div></div>
            <div class="question"><div class="q-title">2. 你获取实习岗位的主要渠道有（可多选）：</div><div class="options" id="channel_group"><label class="checkbox-option"><input type="checkbox" name="channel" value="学校老师/学院推荐"> 学校老师/学院推荐</label><label class="checkbox-option"><input type="checkbox" name="channel" value="校园招聘会、校企合作"> 校园招聘会、校企合作</label><label class="checkbox-option"><input type="checkbox" name="channel" value="正规招聘APP、企业官网"> 正规招聘APP、企业官网</label><label class="checkbox-option"><input type="checkbox" name="channel" value="家人、亲友内推"> 家人、亲友内推</label><label class="checkbox-option"><input type="checkbox" name="channel" value="各类中介机构"> 各类中介机构</label><label class="checkbox-option"><input type="checkbox" name="channel" value="社交媒体、求职社群"> 社交媒体、求职社群</label><label class="checkbox-option"><input type="checkbox" name="channel" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="channel_other_text" placeholder="请注明其他渠道" style="width:220px;"></div></div>
            <div class="question"><div class="q-title">3. 你认为实习经历对求职就业的重要程度：</div><div class="options"><label class="radio-option"><input type="radio" name="importance" value="非常重要，是核心竞争力"> 非常重要，是核心竞争力</label><label class="radio-option"><input type="radio" name="importance" value="比较重要，有一定加分作用"> 比较重要，有一定加分作用</label><label class="radio-option"><input type="radio" name="importance" value="一般，有无影响不大"> 一般，有无影响不大</label><label class="radio-option"><input type="radio" name="importance" value="不重要，可有可无"> 不重要，可有可无</label></div></div>
            <div class="question"><div class="q-title">4. 你是否有寻找名企、优质岗位实习的意愿：</div><div class="options"><label class="radio-option"><input type="radio" name="willingness" value="强烈意愿，全力争取"> 强烈意愿，全力争取</label><label class="radio-option"><input type="radio" name="willingness" value="有一定意愿，尝试投递"> 有一定意愿，尝试投递</label><label class="radio-option"><input type="radio" name="willingness" value="无所谓，有实习即可"> 无所谓，有实习即可</label><label class="radio-option"><input type="radio" name="willingness" value="无意愿，不追求实习"> 无意愿，不追求实习</label></div></div>
        </div>

        <!-- 三、付费实习认知与接触情况 -->
        <div class="section">
            <div class="section-title"><span>三</span> 付费实习认知与接触情况</div>
            <div class="question"><div class="q-title">1. 你是否通过网络、社群、中介、同学等渠道接触过付费实习相关信息：</div><div class="options"><label class="radio-option"><input type="radio" name="contact_info" value="经常接触"> 经常接触</label><label class="radio-option"><input type="radio" name="contact_info" value="偶尔接触"> 偶尔接触</label><label class="radio-option"><input type="radio" name="contact_info" value="极少接触"> 极少接触</label><label class="radio-option"><input type="radio" name="contact_info" value="从未接触"> 从未接触</label></div></div>
            <div class="question"><div class="q-title">2. 你了解到的付费实习收费范围大概是（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="fee_range" value="数千元"> 数千元</label><label class="checkbox-option"><input type="checkbox" name="fee_range" value="1-5万元"> 1-5万元</label><label class="checkbox-option"><input type="checkbox" name="fee_range" value="5-10万元"> 5-10万元</label><label class="checkbox-option"><input type="checkbox" name="fee_range" value="10万元以上"> 10万元以上</label><label class="checkbox-option"><input type="checkbox" name="fee_range" value="不了解"> 不了解</label></div></div>
            <div class="question"><div class="q-title">3. 你是否见过或听闻伪造实习证明、虚构实习岗位、虚假内推等情况：</div><div class="options"><label class="radio-option"><input type="radio" name="fraud_hear" value="经常见过/听闻"> 经常见过/听闻</label><label class="radio-option"><input type="radio" name="fraud_hear" value="偶尔见过/听闻"> 偶尔见过/听闻</label><label class="radio-option"><input type="radio" name="fraud_hear" value="极少见过/听闻"> 极少见过/听闻</label><label class="radio-option"><input type="radio" name="fraud_hear" value="从未见过/听闻"> 从未见过/听闻</label></div></div>
            <div class="question"><div class="q-title">4. 你是否认为付费实习造成了就业机会的不公：</div><div class="options"><label class="radio-option"><input type="radio" name="unfair" value="是"> 是</label><label class="radio-option"><input type="radio" name="unfair" value="否"> 否</label></div></div>
        </div>

        <!-- 四、付费实习参与意愿与行为 -->
        <div class="section">
            <div class="section-title"><span>四</span> 付费实习参与意愿与行为</div>
            <div class="question"><div class="q-title">1. 你是否有过付费购买实习、付费内推的行为：</div><div class="options"><label class="radio-option"><input type="radio" name="pay_behavior" value="有，实际支付过费用"> 有，实际支付过费用</label><label class="radio-option"><input type="radio" name="pay_behavior" value="没有，但有过付费的想法"> 没有，但有过付费的想法</label><label class="radio-option"><input type="radio" name="pay_behavior" value="从未考虑，也不会参与"> 从未考虑，也不会参与</label></div></div>
            <div class="question"><div class="q-title">2. 若你有付费实习的想法或行为，主要原因是（可多选）：</div><div class="options" id="reason_yes_group"><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="就业压力大，优质实习竞争激烈"> 就业压力大，优质实习竞争激烈</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="自身投递多次无回应，走捷径"> 自身投递多次无回应，走捷径</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="身边同学参与，跟风从众"> 身边同学参与，跟风从众</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="想为简历镀金，提升求职竞争力"> 想为简历镀金，提升求职竞争力</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="中介宣传力度大，承诺保offer、保实习证明"> 中介宣传力度大，承诺保offer、保实习证明</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="缺乏正规实习渠道，信息闭塞"> 缺乏正规实习渠道，信息闭塞</label><label class="checkbox-option"><input type="checkbox" name="reason_yes" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="reason_yes_other_text" placeholder="其他原因"></div></div>
            <div class="question"><div class="q-title">3. 若你从未考虑参与付费实习，主要原因是（可多选）：</div><div class="options" id="reason_no_group"><label class="checkbox-option"><input type="checkbox" name="reason_no" value="费用过高，家庭难以承担"> 费用过高，家庭难以承担</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="认为违背公平原则，投机取巧"> 认为违背公平原则，投机取巧</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="担心上当受骗，蒙受经济损失"> 担心上当受骗，蒙受经济损失</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="相信靠自身能力能获取实习机会"> 相信靠自身能力能获取实习机会</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="认为付费实习含金量低，无实际收获"> 认为付费实习含金量低，无实际收获</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="学校禁止，担心受处分"> 学校禁止，担心受处分</label><label class="checkbox-option"><input type="checkbox" name="reason_no" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="reason_no_other_text" placeholder="其他原因"></div></div>
            <div class="question"><div class="q-title">4. 你身边是否有同学、朋友参与付费实习：</div><div class="options"><label class="radio-option"><input type="radio" name="peer_pay" value="较多"> 较多</label><label class="radio-option"><input type="radio" name="peer_pay" value="少数"> 少数</label><label class="radio-option"><input type="radio" name="peer_pay" value="没有"> 没有</label><label class="radio-option"><input type="radio" name="peer_pay" value="不清楚"> 不清楚</label></div></div>
        </div>

        <!-- 五、付费实习乱象危害与成因认知 -->
        <div class="section">
            <div class="section-title"><span>五</span> 付费实习乱象危害与成因认知</div>
            <div class="question"><div class="q-title">1. 你认为付费实习乱象带来的主要危害有哪些（可多选）：</div><div class="options" id="harm_group"><label class="checkbox-option"><input type="checkbox" name="harm" value="破坏教育公平、就业公平，加剧阶层固化"> 破坏教育公平、就业公平，加剧阶层固化</label><label class="checkbox-option"><input type="checkbox" name="harm" value="扰乱正常实习招聘和就业市场秩序"> 扰乱正常实习招聘和就业市场秩序</label><label class="checkbox-option"><input type="checkbox" name="harm" value="加重学生和家庭经济负担"> 加重学生和家庭经济负担</label><label class="checkbox-option"><input type="checkbox" name="harm" value="扭曲大学生价值观，滋生投机心理"> 扭曲大学生价值观，滋生投机心理</label><label class="checkbox-option"><input type="checkbox" name="harm" value="降低人才选拔质量，影响整体人才培养"> 降低人才选拔质量，影响整体人才培养</label><label class="checkbox-option"><input type="checkbox" name="harm" value="滋生灰色产业，诱发诈骗等违法行为"> 滋生灰色产业，诱发诈骗等违法行为</label><label class="checkbox-option"><input type="checkbox" name="harm" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="harm_other_text" placeholder="其他危害"></div></div>
            <div class="question"><div class="q-title">2. 你认为付费实习灰色产业滋生的主要原因是（可多选）：</div><div class="options" id="cause_group"><label class="checkbox-option"><input type="checkbox" name="cause" value="优质实习岗位供不应求，竞争激烈"> 优质实习岗位供不应求，竞争激烈</label><label class="checkbox-option"><input type="checkbox" name="cause" value="高校实习指导不足，缺乏正规实习渠道"> 高校实习指导不足，缺乏正规实习渠道</label><label class="checkbox-option"><input type="checkbox" name="cause" value="企业逃避人才培养责任，不愿提供实习岗位"> 企业逃避人才培养责任，不愿提供实习岗位</label><label class="checkbox-option"><input type="checkbox" name="cause" value="部分学生急功近利，求职心态浮躁"> 部分学生急功近利，求职心态浮躁</label><label class="checkbox-option"><input type="checkbox" name="cause" value="中介和部分企业逐利，勾结牟利"> 中介和部分企业逐利，勾结牟利</label><label class="checkbox-option"><input type="checkbox" name="cause" value="相关法律法规不完善，监管缺位"> 相关法律法规不完善，监管缺位</label><label class="checkbox-option"><input type="checkbox" name="cause" value="就业焦虑和信息不对称"> 就业焦虑和信息不对称</label><label class="checkbox-option"><input type="checkbox" name="cause" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="cause_other_text" placeholder="其他原因"></div></div>
            <div class="question"><div class="q-title">3. 你认为当前针对付费实习乱象的监管力度如何：</div><div class="options"><label class="radio-option"><input type="radio" name="supervision" value="监管严格，乱象得到有效遏制"> 监管严格，乱象得到有效遏制</label><label class="radio-option"><input type="radio" name="supervision" value="监管一般，乱象依然存在"> 监管一般，乱象依然存在</label><label class="radio-option"><input type="radio" name="supervision" value="监管薄弱，乱象泛滥"> 监管薄弱，乱象泛滥</label><label class="radio-option"><input type="radio" name="supervision" value="不清楚相关监管情况"> 不清楚相关监管情况</label></div></div>
        </div>

        <!-- 六、治理诉求与建议（多选板块） -->
        <div class="section">
            <div class="section-title"><span>六</span> 付费实习乱象治理诉求与建议</div>
            <div class="question"><div class="q-title">1. 你认为高校在整治付费实习乱象中应做好哪些工作（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="univ_action" value="搭建正规实习信息平台，拓宽实习渠道"> 搭建正规实习信息平台，拓宽实习渠道</label><label class="checkbox-option"><input type="checkbox" name="univ_action" value="加强实习过程监管，杜绝虚假实习证明"> 加强实习过程监管，杜绝虚假实习证明</label><label class="checkbox-option"><input type="checkbox" name="univ_action" value="开展就业指导，树立正确实习观、就业观"> 开展就业指导，树立正确实习观、就业观</label><label class="checkbox-option"><input type="checkbox" name="univ_action" value="严厉惩处参与付费实习、伪造实习证明的学生"> 严厉惩处参与付费实习、伪造实习证明的学生</label><label class="checkbox-option"><input type="checkbox" name="univ_action" value="加强校企合作，增加优质实习岗位"> 加强校企合作，增加优质实习岗位</label><label class="checkbox-option"><input type="checkbox" name="univ_action" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="univ_action_other_text" placeholder="其他建议"></div></div>
            <div class="question"><div class="q-title">2. 你认为政府部门应采取哪些治理措施（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="gov_action" value="出台专项法律法规，明确付费实习违法违规"> 出台专项法律法规，明确付费实习违法违规</label><label class="checkbox-option"><input type="checkbox" name="gov_action" value="加大监管执法力度，严查中介和违规企业"> 加大监管执法力度，严查中介和违规企业</label><label class="checkbox-option"><input type="checkbox" name="gov_action" value="打击虚假实习、伪造实习证明等行为"> 打击虚假实习、伪造实习证明等行为</label><label class="checkbox-option"><input type="checkbox" name="gov_action" value="统筹增加公益性实习、见习岗位"> 统筹增加公益性实习、见习岗位</label><label class="checkbox-option"><input type="checkbox" name="gov_action" value="完善实习生权益保障制度"> 完善实习生权益保障制度</label><label class="checkbox-option"><input type="checkbox" name="gov_action" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="gov_action_other_text" placeholder="其他措施"></div></div>
            <div class="question"><div class="q-title">3. 你认为企业应承担哪些责任（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="corp_action" value="主动提供正规实习岗位，履行人才培养责任"> 主动提供正规实习岗位，履行人才培养责任</label><label class="checkbox-option"><input type="checkbox" name="corp_action" value="杜绝与中介勾结牟利，规范实习招聘"> 杜绝与中介勾结牟利，规范实习招聘</label><label class="checkbox-option"><input type="checkbox" name="corp_action" value="公开透明招聘流程，杜绝内推暗箱操作"> 公开透明招聘流程，杜绝内推暗箱操作</label><label class="checkbox-option"><input type="checkbox" name="corp_action" value="加强实习生管理和培养，提升实习含金量"> 加强实习生管理和培养，提升实习含金量</label><label class="checkbox-option"><input type="checkbox" name="corp_action" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="corp_action_other_text" placeholder="其他责任"></div></div>
            <div class="question"><div class="q-title">4. 你认为实习中介该如何规范自身行为（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="agency_action" value="杜绝售卖实习岗位、付费内推等违规业务"> 杜绝售卖实习岗位、付费内推等违规业务</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="发布真实合规的实习信息，不虚构岗位、不做虚假承诺"> 发布真实合规的实习信息，不虚构岗位、不做虚假承诺</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="合理收取服务费用，明码标价，杜绝天价收费"> 合理收取服务费用，明码标价，杜绝天价收费</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="坚守行业底线，不与企业内部人员勾结牟利"> 坚守行业底线，不与企业内部人员勾结牟利</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="仅提供求职咨询、简历指导等正规服务，不插手实习内推"> 仅提供求职咨询、简历指导等正规服务，不插手实习内推</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="主动接受监管，公示资质和服务范围"> 主动接受监管，公示资质和服务范围</label><label class="checkbox-option"><input type="checkbox" name="agency_action" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="agency_action_other_text" placeholder="其他建议"></div></div>
            <div class="question"><div class="q-title">5. 你认为自身应如何抵制付费实习乱象（可多选）：</div><div class="options"><label class="checkbox-option"><input type="checkbox" name="self_action" value="树立公平竞争意识，拒绝投机捷径"> 树立公平竞争意识，拒绝投机捷径</label><label class="checkbox-option"><input type="checkbox" name="self_action" value="提高警惕，谨防实习诈骗"> 提高警惕，谨防实习诈骗</label><label class="checkbox-option"><input type="checkbox" name="self_action" value="不参与、不传播付费实习信息"> 不参与、不传播付费实习信息</label><label class="checkbox-option"><input type="checkbox" name="self_action" value="提升自身能力，靠实力争取实习机会"> 提升自身能力，靠实力争取实习机会</label><label class="checkbox-option"><input type="checkbox" name="self_action" value="主动举报违规付费实习行为"> 主动举报违规付费实习行为</label><label class="checkbox-option"><input type="checkbox" name="self_action" value="其他"> 其他</label></div><div class="other-input"><input type="text" id="self_action_other_text" placeholder="其他做法"></div></div>
            <div class="question"><div class="q-title">6. 对于治理大学生付费实习乱象，你还有其他意见或建议吗？</div><textarea name="suggestions" rows="3" style="width:100%; padding:12px; border-radius:20px; border:1px solid #cbd5e1; font-family:inherit;" placeholder="欢迎分享您的宝贵建议……"></textarea></div>
        </div>

        <div style="display: flex; flex-wrap: wrap; gap: 12px; margin-top: 20px;">
            <button type="button" id="submitBtn">📬 提交问卷 (导出结果)</button>
            <button type="button" id="resetBtn" class="btn-secondary">🗑️ 重置表单</button>
        </div>
        <div class="footer-note">
            * 本问卷提交后将生成答卷数据，支持下载为JSON文件，研究者可汇总分析。所有数据仅用于学术研究，请放心填写。
        </div>
    </form>
</div>

<script>
    // 生成当前页面URL的二维码 (部署后自动为线上链接)
    let currentUrl = window.location.href;
    // 如果是本地file协议，提示但依然生成
    if (currentUrl.startsWith('file://')) {
        document.getElementById('qrcode').innerHTML = '<div style="font-size:12px;text-align:center;">📁 本地文件<br>部署后扫码</div>';
    } else {
        new QRCode(document.getElementById("qrcode"), {
            text: currentUrl,
            width: 100,
            height: 100,
            colorDark: "#1f6e5c",
            colorLight: "#ffffff",
            correctLevel: QRCode.CorrectLevel.M
        });
    }

    // 辅助函数：获取多选值（带自定义其他文本）
    function getCheckboxValues(groupName, otherId = null) {
        let values = [];
        document.querySelectorAll(`input[name="${groupName}"]:checked`).forEach(cb => {
            let val = cb.value;
            if (val === '其他' && otherId) {
                let otherVal = document.getElementById(otherId)?.value.trim();
                if (otherVal) val = `其他: ${otherVal}`;
            }
            values.push(val);
        });
        return values;
    }

    // 获取单选值
    function getRadioValue(name) {
        let selected = document.querySelector(`input[name="${name}"]:checked`);
        return selected ? selected.value : null;
    }

    // 收集所有问卷数据
    function collectData() {
        let data = {};

        // 基本信息
        data.gender = getRadioValue('gender');
        data.grade = getRadioValue('grade');
        data.univ_level = getRadioValue('univ_level');
        data.major = getRadioValue('major');
        data.plan = getRadioValue('plan');
        data.family_eco = getRadioValue('family_eco');
        data.intern_exp = getRadioValue('intern_exp');
        // 渠道多选
        let channels = getCheckboxValues('channel', 'channel_other_text');
        data.channels = channels;
        data.importance = getRadioValue('importance');
        data.willingness = getRadioValue('willingness');
        data.contact_info = getRadioValue('contact_info');
        data.fee_range = getCheckboxValues('fee_range');
        data.fraud_hear = getRadioValue('fraud_hear');
        data.unfair = getRadioValue('unfair');
        data.pay_behavior = getRadioValue('pay_behavior');
        data.reason_yes = getCheckboxValues('reason_yes', 'reason_yes_other_text');
        data.reason_no = getCheckboxValues('reason_no', 'reason_no_other_text');
        data.peer_pay = getRadioValue('peer_pay');
        data.harm = getCheckboxValues('harm', 'harm_other_text');
        data.cause = getCheckboxValues('cause', 'cause_other_text');
        data.supervision = getRadioValue('supervision');
        data.univ_action = getCheckboxValues('univ_action', 'univ_action_other_text');
        data.gov_action = getCheckboxValues('gov_action', 'gov_action_other_text');
        data.corp_action = getCheckboxValues('corp_action', 'corp_action_other_text');
        data.agency_action = getCheckboxValues('agency_action', 'agency_action_other_text');
        data.self_action = getCheckboxValues('self_action', 'self_action_other_text');
        let suggestions = document.querySelector('textarea[name="suggestions"]')?.value || '';
        data.suggestions = suggestions;

        return data;
    }

    // 导出JSON并下载
    function downloadJSON(data) {
        const jsonStr = JSON.stringify(data, null, 2);
        const blob = new Blob([jsonStr], {type: "application/json"});
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = `internship_survey_${new Date().toISOString().slice(0,19)}.json`;
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
    }

    // 展示预览并导出
    function handleSubmit() {
        const result = collectData();
        // 简单校验必填？可适当提醒，但为了体验仅做温和提示
        if (!result.gender) { alert('请至少填写性别'); return; }
        if (!result.grade) { alert('请填写年级'); return; }
        // 其余非强制但为了学术完整性提醒核心字段
        let confirmMsg = "问卷已填写完毕，即将导出数据文件（JSON）。\n您可以将该文件交给研究者汇总。";
        if (confirm(confirmMsg)) {
            downloadJSON(result);
            alert("✅ 数据已导出！感谢您的参与。");
        }
    }

    function resetForm() {
        if (confirm('确定要重置所有已填内容吗？')) {
            document.getElementById('surveyForm').reset();
            // 清空所有额外的 other 输入框
            let otherInputs = document.querySelectorAll('.other-input input');
            otherInputs.forEach(inp => inp.value = '');
        }
    }

    document.getElementById('submitBtn').addEventListener('click', handleSubmit);
    document.getElementById('resetBtn').addEventListener('click', resetForm);
</script>
</body>
</html>
