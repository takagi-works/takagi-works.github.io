---
layout: page
title: "[箱] Hako" 
permalink: /hako.html
eyebrow: Project spotlight
lead: Ruby runtime for Zephyr RTOS built on mruby/c, with optional on-device compilation via PicoRuby.
---
<div class="content-block">
  <h2>Purpose</h2>
  <p>Hako (箱, “box”) brings Ruby directly onto constrained devices. It packages mruby/c, PicoRuby, and a minimal Zephyr integration so you can script hardware, prototype logic, and ship production-ready bytecode without pulling extra dependencies onto the device.</p>
</div>

<div class="section-grid">
  <div class="card">
    <h2>Highlights</h2>
    <ul>
      <li>mruby/c VM (~40 KB ROM/40 KB RAM) with PicoRuby compiler optional for on-device compile.</li>
      <li>Interactive shell (IRB-like) to run Ruby snippets and inspect the VM.</li>
      <li>Filesystem support (LittleFS/FAT) to load scripts; package system for require/load.</li>
      <li>Extensible: write C extensions with Ruby bindings; Zephyr GPIO module included.</li>
      <li>Highly configurable: scale from minimal VM-only builds to full dev environments.</li>
    </ul>
  </div>
  <div class="card">
    <h2>How to explore</h2>
    <p>Drop the module under <code>modules/lib/hako/</code> in your Zephyr workspace, set a handful of Kconfig flags, and build for your board or QEMU. Start with VM-only, then enable the compiler and shell when you need interactive Ruby.</p>
    <a class="button" href="https://github.com/takagi-works/hako">View on GitHub</a>
  </div>
</div>

<div class="content-block">
  <h2>Quick start on Zephyr</h2>
  <p>Minimal VM (pre-compiled bytecode) versus full interactive mode. Toggle features through Kconfig.</p>
  <pre><code># prj.conf (minimal VM-only, small footprint)
CONFIG_HAKO=y
CONFIG_HAKO_MEMORY_SIZE=32768

# prj.conf (interactive with compiler + shell)
CONFIG_HAKO=y
CONFIG_HAKO_COMPILER=y
CONFIG_HAKO_EVAL=y
CONFIG_HAKO_IRB_COMMAND=y
CONFIG_SHELL=y
CONFIG_HEAP_MEM_POOL_SIZE=131072
CONFIG_MAIN_STACK_SIZE=4096

# Build and run (example: QEMU)
west build -b qemu_x86
west build -t run

# In the shell
uart:~$ ruby "puts 'Hello from Hako'"
uart:~$ ruby_info
</code></pre>
</div>

<div class="content-block">
  <h2>What’s next</h2>
  <p>The roadmap focuses on richer API integration of Zephyr RTOS. Watch the repo for releases or check the blog for deeper walkthroughs.</p>
</div>
