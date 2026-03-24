---
title: "主页"
---

<div class="hero">
  <h1>House_of_Fan</h1>
  <p>算法竞赛 · 技术笔记 · 生活随笔</p>
</div>

<div class="recent-posts">
  <h2>📌 最新文章推荐</h2>
  <div class="post-list">
    {{ range first 3 (where .Site.RegularPages "Section" "posts") }}
    <div class="post-card">
      <h3><a href="{{ .Permalink }}">{{ .Title }}</a></h3>
      <div class="post-meta">
        <time>{{ .Date.Format "2006-01-02" }}</time>
        {{ with .Params.categories }}
        <span class="categories">
          {{ range . }}
          <span class="category">{{ . }}</span>
          {{ end }}
        </span>
        {{ end }}
      </div>
      <p>{{ .Summary | truncate 120 }}</p>
    </div>
    {{ end }}
  </div>
</div>

<style>
.hero {
  text-align: center;
  padding: 4rem 1rem;
  margin-bottom: 2rem;
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(8px);
  border-radius: 24px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
  color: #1a1a2e;
}

.hero p {
  font-size: 1.2rem;
  color: #2c3e66;
}

.recent-posts {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(5px);
  border-radius: 24px;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.recent-posts h2 {
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  border-left: 5px solid #1e88e5;
  padding-left: 1rem;
}

.post-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

.post-card {
  background: rgba(255, 255, 255, 0.6);
  border-radius: 16px;
  padding: 1.2rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.post-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  background: rgba(255, 255, 255, 0.9);
}

.post-card h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.2rem;
}

.post-card h3 a {
  text-decoration: none;
  color: #1e466e;
}

.post-meta {
  font-size: 0.85rem;
  color: #666;
  margin-bottom: 0.75rem;
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.category {
  background: #e0e7ff;
  padding: 0.2rem 0.6rem;
  border-radius: 20px;
  font-size: 0.75rem;
  color: #1e3a8a;
}

.dark .hero {
  background: rgba(0, 0, 0, 0.6);
  border-color: rgba(255, 255, 255, 0.2);
}
.dark .hero h1 { color: #f0f0f0; }
.dark .hero p { color: #cccccc; }
.dark .recent-posts { background: rgba(30, 30, 40, 0.85); }
.dark .post-card { background: rgba(40, 40, 55, 0.6); }
.dark .post-card:hover { background: rgba(50, 50, 70, 0.9); }
.dark .post-card h3 a { color: #90caf9; }
.dark .category { background: #2d3748; color: #a0c4ff; }
</style>
