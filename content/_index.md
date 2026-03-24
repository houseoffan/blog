---
title: "主页"
---

<style>
.hero-section {
  text-align: center;
  padding: 60px 20px;
  background: rgba(255, 255, 255, 0.85);
  border-radius: 24px;
  margin-bottom: 40px;
  backdrop-filter: blur(8px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
}

.hero-section h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
  color: #1a1a2e;
}

.hero-section p {
  font-size: 1.2rem;
  color: #4a5568;
}

.posts-section {
  background: rgba(255, 255, 255, 0.9);
  border-radius: 24px;
  padding: 30px;
  backdrop-filter: blur(5px);
}

.posts-section h2 {
  font-size: 1.8rem;
  margin-bottom: 25px;
  border-left: 4px solid #1e88e5;
  padding-left: 15px;
}

.post-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}

.post-card {
  background: white;
  border-radius: 16px;
  padding: 20px;
  transition: transform 0.2s;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}

.post-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
}

.post-card h3 {
  margin: 0 0 10px 0;
  font-size: 1.2rem;
}

.post-card h3 a {
  text-decoration: none;
  color: #1e466e;
}

.post-meta {
  font-size: 0.85rem;
  color: #718096;
  margin-bottom: 10px;
}

.post-excerpt {
  font-size: 0.9rem;
  color: #4a5568;
  line-height: 1.5;
}

.dark .hero-section {
  background: rgba(30, 30, 40, 0.85);
}

.dark .hero-section h1 {
  color: #f0f0f0;
}

.dark .hero-section p {
  color: #cbd5e0;
}

.dark .posts-section {
  background: rgba(30, 30, 40, 0.9);
}

.dark .post-card {
  background: #2d3748;
}

.dark .post-card h3 a {
  color: #90caf9;
}

.dark .post-meta {
  color: #a0aec0;
}

.dark .post-excerpt {
  color: #cbd5e0;
}
</style>

<div class="hero-section">
  <h1>🚀 House_of_Fan</h1>
  <p>算法竞赛 · 技术笔记 · 生活随笔</p>
</div>

<div class="posts-section">
  <h2>📌 最新文章推荐</h2>
  <div class="post-grid">
    {{ range first 3 (where .Site.RegularPages "Section" "posts") }}
    <div class="post-card">
      <h3><a href="{{ .Permalink }}">{{ .Title }}</a></h3>
      <div class="post-meta">
        📅 {{ .Date.Format "2006-01-02" }}
        {{ with .Params.categories }}
        | 🏷️ {{ index . 0 }}
        {{ end }}
      </div>
      <div class="post-excerpt">
        {{ .Summary | truncate 100 }}
      </div>
    </div>
    {{ else }}
    <div class="post-card">
      <p>暂无文章，即将更新！</p>
    </div>
    {{ end }}
  </div>
</div>
