---
layout: default
---

<div class="hero-personal">
  <div class="container">
    <div class="hero-content">
      <div class="hero-info-wrapper">
        <div class="hero-text">
           <h1 class="hero-name">{{ site.author | default: "Your Name" }}</h1>
           <p class="hero-title">Robotics & Mechatronics</p>
           <p>
            Welcome to my portfolio website! I am a second year master's student in Robotics at New York University. I am interested in Robotics, automation, and AI, everything that makes machines move and act intelligently. 
            <p> I am particularly interested in <span style="color: white; font-weight: bold;"> dynamics and control, and machine-learning methods</span> for control. I am passionate about Reinforcement Learning,and methods for efficient first-order model-based RL and contrained RL, which enable more robust and safe RL.</p>
            <!-- I am passionate about Reinforcement Learning, specifically efficient first-order model-based methods and constrained RL, which facilitate the development of robust, safety-critical systems. -->
           </p>
        </div>
        
        <div class="hero-actions">
          <!-- <a href="{{ '/about/' | relative_url }}" class="btn-secondary">
            About
          </a> -->
           <a href="#contact-email" class="btn-secondary">
            Contact
          </a>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="projects-showcase">
  <div class="container">
    <div class="section-header">
      <h2>Project Highlights</h2>
      <p class="section-subtitle">A selection of major projects and research</p>
    </div>
    
    <div class="projects-grid-featured">
      {% assign featured_projects = site.projects | where: "featured", true | sort: "date" | reverse %}
      {% assign all_projects = site.projects | sort: "date" | reverse %}
      {% assign combined_projects = featured_projects | concat: all_projects %}
      {% assign unique_projects = combined_projects | uniq %}
      {% for project in unique_projects limit: 9 %}
        <div class="project-card-featured">
          <div class="project-media">
            {% if project.featured_image %}
              <img src="{{ project.featured_image | relative_url }}" alt="{{ project.title }}" class="project-image">
            {% elsif project.models.first %}
              <div class="model-preview-small">
                <model-viewer 
                  src="{{ project.models.first.file | relative_url }}"
                  alt="{{ project.title }}"
                  camera-controls
                  auto-rotate
                  class="preview-model-small">
                </model-viewer>
              </div>
            {% else %}
              <div class="project-placeholder-small">
                <i class="fas fa-robot"></i>
              </div>
            {% endif %}
            
            <div class="project-overlay">
              <a href="{{ project.url | relative_url }}" class="project-link-overlay">
                <i class="fas fa-arrow-right"></i>
              </a>
            </div>
          </div>
          
          <div class="project-info-featured">
            <div class="project-categories-small">
              {% for category in project.categories limit:2 %}
                <span class="category-tag-small">{{ category }}</span>
              {% endfor %}
            </div>
            
            <h3 class="project-title-featured">
              <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
            </h3>
            
            <p class="project-excerpt-small">{{ project.description | truncate: 80 }}</p>
            
            <div class="project-features-small">
              {% if project.models %}
                <span class="feature-badge-small" title="3D Models">
                  <i class="fas fa-cube"></i>
                  {{ project.models.size }}
                </span>
              {% endif %}
              
              {% if project.schematics %}
                <span class="feature-badge-small" title="Schematics">
                  <i class="fas fa-microchip"></i>
                  {{ project.schematics.size }}
                </span>
              {% endif %}
              
              {% if project.code_files %}
                <span class="feature-badge-small" title="Code Files">
                  <i class="fas fa-code"></i>
                  {{ project.code_files.size }}
                </span>
              {% endif %}
            </div>
          </div>
        </div>
      {% endfor %}
    </div>
    
    <div class="showcase-actions">
      <a href="{{ '/projects/' | relative_url }}" class="btn-primary-large">
        <i class="fas fa-th"></i>
        View All Projects
      </a>
    </div>
  </div>
</div>

<div class="skills-section">
  <div class="container">
    <div class="skills-content">
      <h2>Technical Expertise</h2>
      <div class="skills-grid">
        <div class="skill-category">
          <h3><i class="fas fa-robot"></i> Robotics</h3>
          <div class="skill-tags">
            <span class="skill-tag">ROS</span>
            <span class="skill-tag">Kinematics</span>
            <span class="skill-tag">Path Planning</span>
            <span class="skill-tag">SLAM</span>
          </div>
        </div>
        <div class="skill-category">
          <h4><i class="fas fa-microchip"></i> Electronics & Embedded Systems</h4>
          <div class="skill-tags">
            <span class="skill-tag">Arduino</span>
            <span class="skill-tag">ESP32</span>
            <span class="skill-tag">PCB Design</span>
            <span class="skill-tag">Sensors</span>
          </div>
        </div>
        <div class="skill-category">
          <h3><i class="fas fa-code"></i> Programming</h3>
          <div class="skill-tags">
            <span class="skill-tag">Python</span>
            <span class="skill-tag">C/C++</span>
            <span class="skill-tag">MATLAB</span>
            <span class="skill-tag">JavaScript</span>
          </div>
        </div>
        <div class="skill-category">
          <h4><i class="fas fa-cube"></i> CAD & Rapid Prototyping</h4>
          <div class="skill-tags">
            <span class="skill-tag">SolidWorks</span>
            <span class="skill-tag">Fusion 360</span>
            <span class="skill-tag">3D Printing</span>
            <span class="skill-tag">KiCad</span>
          </div>
        </div>

        <div class="skill-category">
          <h4><i class="fas fa-cube"></i> Machine Learning</h4>
          <div class="skill-tags">
            <span class="skill-tag">SolidWorks</span>
            <span class="skill-tag">Fusion 360</span>
            <span class="skill-tag">3D Printing</span>
            <span class="skill-tag">KiCad</span>
          </div>
        </div>

        <div class="skill-category">
          <h3><i class="fas fa-cube"></i> Simulation</h3>
          <div class="skill-tags">
            <span class="skill-tag">IsaacSim</span>
            <span class="skill-tag">MuJoCo</span>
            <span class="skill-tag">Genesis</span>
            <span class="skill-tag">Simulink</span>
            <span class="skill-tag">Simscape</span>
            <span class="skill-tag">Gazebo</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
