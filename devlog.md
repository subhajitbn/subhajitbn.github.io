---
layout: default
title: Devlog
permalink: /devlog/
---

<section class="devlog-stream">
    <h2>Development Log</h2>
    <p>Short-form updates, build notes, and work in progress.</p>

    {% assign sorted_logs = site.devlog | sort: 'date' | reverse %}
    
    {% for log in sorted_logs %}
        <article class="miniblog-entry" style="border-left: 3px solid #333; padding-left: 15px; margin-bottom: 2rem;">
            <time datetime="{{ log.date | date_to_xmlschema }}" style="font-size: 0.85em; color: #666;">
                {{ log.date | date: "%B %d, %Y • %H:%M" }}
            </time>
            
            <div class="miniblog-content">
                {{ log.content }} 
            </div>
            
            <a href="{{ log.url }}" style="font-size: 0.8em; text-decoration: none;"># Permalink</a>
        </article>
    {% endfor %}
</section>
