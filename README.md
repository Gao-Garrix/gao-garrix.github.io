<!--# Welcome to Gao-Garrix's homepage!-->

<div align="center">
  <h1>Welcome to Gao Garrix's Personal Website</h1>
  <p>此网站用于分享我的学习笔记与技术探索</p>
  <p>所有技术文章均按照分类组织，点击分类可查看相关主题的所有文章</p>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/C++/C-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++/C">
  <img src="https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="Go">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis">
  <img src="https://img.shields.io/badge/Kafka-231F20?style=for-the-badge&logo=apache-kafka&logoColor=white" alt="Kafka">
  <img src="https://img.shields.io/badge/NATS-00BCD4?style=for-the-badge&logo=nats&logoColor=white" alt="NATS">
  <img src="https://img.shields.io/badge/gRPC-00599C?style=for-the-badge&logo=grpc&logoColor=white" alt="gRPC">
</div>

<style>
.bubble-container {
  position: relative;
  width: 100%;
  height: 400px;
  overflow: hidden;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 10px;
  margin: 20px 0;
}

.bubble {
  position: absolute;
  border-radius: 50%;
  opacity: 0.7;
  animation: float 8s infinite ease-in-out;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  25% {
    transform: translateY(-20px) translateX(10px);
  }
  50% {
    transform: translateY(10px) translateX(-10px);
  }
  75% {
    transform: translateY(-10px) translateX(5px);
  }
}

.tech-bubble {
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-weight: bold;
  font-size: 16px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.tech-bubble:hover {
  transform: scale(1.1);
  opacity: 0.9;
}

/* 不同技术的颜色 */
.cpp { background-color: #00599C; }
.go { background-color: #00ADD8; }
.mysql { background-color: #4479A1; }
.redis { background-color: #DC382D; }
.kafka { background-color: #231F20; }
.nats { background-color: #00BCD4; }
.grpc { background-color: #00599C; }

/* 响应式设计 */
@media (max-width: 768px) {
  .bubble-container {
    height: 300px;
  }
  .tech-bubble {
    font-size: 14px;
  }
}
</style>

<div class="bubble-container">
  <!-- C++/C 气泡 -->
  <div class="bubble tech-bubble cpp" style="width: 120px; height: 120px; top: 20%; left: 10%; animation-delay: 0s;">C++/C</div>
  
  <!-- Go 气泡 -->
  <div class="bubble tech-bubble go" style="width: 100px; height: 100px; top: 50%; left: 25%; animation-delay: 1s;">Go</div>
  
  <!-- MySQL 气泡 -->
  <div class="bubble tech-bubble mysql" style="width: 110px; height: 110px; top: 30%; left: 45%; animation-delay: 2s;">MySQL</div>
  
  <!-- Redis 气泡 -->
  <div class="bubble tech-bubble redis" style="width: 90px; height: 90px; top: 60%; left: 60%; animation-delay: 3s;">Redis</div>
  
  <!-- Kafka 气泡 -->
  <div class="bubble tech-bubble kafka" style="width: 130px; height: 130px; top: 15%; left: 75%; animation-delay: 4s;">Kafka</div>
  
  <!-- NATS 气泡 -->
  <div class="bubble tech-bubble nats" style="width: 95px; height: 95px; top: 45%; left: 85%; animation-delay: 5s;">NATS</div>
  
  <!-- gRPC 气泡 -->
  <div class="bubble tech-bubble grpc" style="width: 105px; height: 105px; top: 70%; left: 40%; animation-delay: 6s;">gRPC</div>
  
  <!-- 装饰性气泡 -->
  <div class="bubble" style="width: 60px; height: 60px; background-color: rgba(255, 255, 255, 0.3); top: 10%; left: 5%; animation-delay: 0.5s;"></div>
  <div class="bubble" style="width: 40px; height: 40px; background-color: rgba(255, 255, 255, 0.2); top: 80%; left: 15%; animation-delay: 1.5s;"></div>
  <div class="bubble" style="width: 50px; height: 50px; background-color: rgba(255, 255, 255, 0.25); top: 25%; left: 65%; animation-delay: 2.5s;"></div>
  <div class="bubble" style="width: 30px; height: 30px; background-color: rgba(255, 255, 255, 0.2); top: 75%; left: 30%; animation-delay: 3.5s;"></div>
  <div class="bubble" style="width: 45px; height: 45px; background-color: rgba(255, 255, 255, 0.3); top: 55%; left: 90%; animation-delay: 4.5s;"></div>
</div>

<div align="center">
  <h3>关于我</h3>
  <p>南京邮电大学 | 技术爱好者 | 代码探索者</p>
  <p>在这里分享我的学习笔记、项目经验和技术探索</p>
</div>

<div align="center">
  <h3>博客结构</h3>
  <p>本博客基于 Jekyll 构建，所有文章均存储在 <code>_posts</code> 目录下</p>
  <p>文章按照技术领域分类，包括但不限于：C++、Golang、MySQL、Redis、Docker、Kafka 等</p>
  <p>点击主页上的分类链接或访问 <a href="{{ site.baseurl }}/categories.html">分类页面</a> 可查看所有分类</p>
</div>

<div align="center">
  <h3>联系方式</h3>
  <p>邮箱: junnmail@163.com</p>
  <p>GitHub: <a href="https://github.com/gao-garrix" target="_blank">github.com/gao-garrix</a></p>
</div>

<div align="center">
  <h3>技术专题</h3>
  <a href="{{ site.baseurl }}/categories/C++">C++</a> |
  <a href="{{ site.baseurl }}/categories/Golang">Golang</a> |
  <a href="{{ site.baseurl }}/categories/MySQL">MySQL</a> |
  <a href="{{ site.baseurl }}/categories/Redis">Redis</a> |
  <a href="{{ site.baseurl }}/categories/Kafka">Kafka</a> |
  <a href="{{ site.baseurl }}/categories/Docker">Docker</a>
</div>

<div align="center">
  <h3>如何贡献文章</h3>
  <p>欢迎提交技术文章到本博客！</p>
  <p>1. 在 <code>_posts</code> 目录下创建新的 Markdown 文件</p>
  <p>2. 在文件头部添加 Front Matter，指定文章标题、日期和分类</p>
  <p>3. 文件命名格式为：<code>YYYY-MM-DD-文章标题.md</code></p>
  <p>4. 提交 Pull Request 到本仓库</p>
</div>
