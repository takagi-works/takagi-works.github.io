---
layout: page
title: "[波] Takagi"
permalink: /takagi.html
eyebrow: Project spotlight
lead: Lightweight Sinatra-like CoAP framework for Ruby, built for IoT APIs and microservices.
---
<div class="content-block">
  <h2>Purpose</h2>
  <p>Takagi treats CoAP as a first-class web protocol. If you can build an HTTP API, you can build a CoAP API: routes, middleware, helpers, and discovery metadata all feel like Sinatra while staying efficient for constrained environments.</p>
</div>

<div class="section-grid">
  <div class="card">
    <h2>Highlights</h2>
    <ul>
      <li>Minimal DSL for GET/POST/PUT/DELETE plus Observe with the same semantics as HTTP.</li>
      <li>Inline CoRE discovery helpers to configure <code>/.well-known/core</code> metadata.</li>
      <li>Runs over UDP by default with CoAP over TCP (RFC 8323) when you need reliability.</li>
      <li>Built-in response, error, validation, and request helpers to keep handlers concise.</li>
      <li>Client API with JSON helpers and readable output for quick inspection.</li>
    </ul>
  </div>
  <div class="card">
    <h2>How to explore</h2>
    <p>Gem install or add to your Gemfile, then start with a single endpoint and expand into sensor data, device control, or microservice messaging.</p>
    <a class="button" href="https://github.com/takagi-works/takagi">View on GitHub</a>
  </div>
</div>

<div class="content-block">
  <h2>Quick start</h2>
  <p>Define a CoAP API that feels like Sinatra. Serve over UDP by default, with TCP when needed.</p>
  <pre><code>gem install takagi
require 'takagi'

class SensorAPI &lt; Takagi::Base
  get '/sensor/:id' do
    json id: params[:id], value: 22.5, status: 'active'
  end

  post '/sensor' do
    validate_params :value
    created sensor_id: rand(1000), value: params[:value]
  end

  reactor do
    observable '/sensors/temp' do
      core { rt 'sensor.temp.streaming' }
      json temp: 42.0, unit: 'celsius'
    end
  end
end

SensorAPI.run!(protocols: [:udp, :tcp])
</code></pre>
</div>

<div class="content-block">
  <h2>What’s next</h2>
  <p>The roadmap focuses on richer discovery helpers, expanded client ergonomics, and more examples for Observe-heavy scenarios. Watch the repo for releases or check the blog for deeper walkthroughs.</p>
</div>
