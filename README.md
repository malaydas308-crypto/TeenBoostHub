{t:'Have boundaries of your own',d:'Saying no to things that don\'t serve you = self-respect = attractive.',tag:'Confidence'},
      {t:'Make plans and follow through',d:'"I know a great place for this â€” I\'ll take you Friday." Then do it.',tag:'Initiative'},
      {t:'Be curious about her life and opinions',d:'"What do you think about that?" + actually listening = deeper than most relationships ever get.',tag:'Connection'},
      {t:'Have gratitude that you express',d:'"This is such a good day" â€” expressed appreciation creates warmth around you.',tag:'Energy'},
      {t:'Be non-judgmental about her past',d:'Judging what came before you = insecurity. Rise above it.',tag:'Maturity'},
      {t:'Have a strong sense of identity',d:'Know who you are. What you like. What you won\'t compromise on. Identity is magnetic.',tag:'Confidence'},
      {t:'Work on your communication skills',d:'Expressing yourself clearly and honestly saves every relationship.',tag:'Communication'},
      {t:'Be the one who deescalates arguments',d:'"Let\'s step back" = strength. Matching fire with fire = immaturity.',tag:'Maturity'},
      {t:'Develop patience as a superpower',d:'Patience in frustrating moments = rare. People notice and remember.',tag:'Character'},
      {t:'Have plans for your future',d:'Knowing roughly where you\'re headed is deeply reassuring.',tag:'Ambition'},
      {t:'Create memorable experiences together',d:'The couple who does interesting things together has more to hold on to.',tag:'Lifestyle'},
      {t:'Know when to be the support',d:'Sometimes she needs you to listen â€” not fix. Learn to tell the difference.',tag:'EQ'},
      {t:'Respect her opinions even when you disagree',d:'"I see it differently but I hear what you\'re saying" = mature communication.',tag:'Respect'},
      {t:'Have a long-term vision for yourself',d:'Ambition beyond today = depth of character beyond average.',tag:'Ambition'},
      {t:'Be interesting to talk to at any hour',d:'3am conversations matter. Be someone worth staying up for.',tag:'Personality'},
      {t:'Show up when things are hard',d:'Anyone can be present in good times. The hard times reveal character.',tag:'Character'},
      {t:'Be vulnerable first',d:'Being the first to share something real gives her permission to be real too.',tag:'Vulnerability'},
      {t:'Know how to apologise and repair',d:'Conflict is inevitable. Repair is a skill. Learn it.',tag:'Maturity'},
      {t:'Never stop being curious about her',d:'Long after the start, ask new questions. People grow. Stay curious.',tag:'Connection'},
      {t:'Prioritise her without losing yourself',d:'She should feel valued but you should still be a full, independent person.',tag:'Balance'},
      {t:'Celebrate what makes her different',d:'Tell her specifically why her uniqueness is what you love most.',tag:'Connection'},
      {t:'Be someone she can brag about',d:'Not for ego â€” but because your values, work and character make her proud.',tag:'Character'},
      {t:'Be honest about your feelings',d:'Saying "I like spending time with you" early is brave and attractive.',tag:'Vulnerability'},
      {t:'Protect the relationship\'s energy',d:'Don\'t complain about her to others. What\'s between you stays between you.',tag:'Trust'},
      {t:'Be the reason she smiles unexpectedly',d:'A random text. A small gift. Noticing something. Small = big.',tag:'Thoughtfulness'},
      {t:'Work on your past traumas',d:'Unprocessed hurt becomes unfair burden. Doing the work = respecting her.',tag:'Mental Health'},
      {t:'Be consistent in your care',d:'Not just on good days or when you want something. Every day. Consistently.',tag:'Character'},
      {t:'Develop a rich inner world',d:'Reading, reflection, journalling â€” depth of self creates depth in connection.',tag:'Intelligence'},
      {t:'Have a clear sense of your values',d:'What you stand for. What you won\'t accept. What matters most. Know it.',tag:'Values'},
      {t:'Treat every woman with respect',d:'Not just her â€” all women. She\'s watching how you treat others.',tag:'Respect'},
      {t:'Know how to give a real hug',d:'Present, warm, unhurried. Physical safety starts here.',tag:'Physical'},
      {t:'Make her feel like the most interesting person',d:'Focus on her like she\'s fascinating. Because she is.',tag:'Attention'},
      {t:'Be the same person in public and private',d:'Consistency across contexts = no performance = authentic = safe.',tag:'Authenticity'},
      {t:'Have a long-term friendship with someone',d:'A 10-year friendship shows you can love and be loyal long-term.',tag:'Character'},
      {t:'Know when to give advice and when to just hold space',d:'"Do you want me to help solve this or do you just need to vent?"',tag:'EQ'},
      {t:'Grow in wisdom, not just in age',d:'Reflect on experiences. Draw lessons. Apply them. Age without wisdom is just ageing.',tag:'Growth'},
      {t:'Be someone she\'s proud to introduce',d:'Your character, manner and warmth should make her proud to say "this is him."',tag:'Character'},
      {t:'Accept love without deflecting it',d:'Let compliments land. Don\'t self-deprecate out of insecurity.',tag:'Self-Worth'},
      {t:'Build a life she\'d want to be part of',d:'Interesting work, real friends, growth, joy. Build that. Invitation follows naturally.',tag:'Lifestyle'},
      {t:'Love yourself enough to let her love you too',d:'Self-love isn\'t arrogance. It\'s the foundation of every healthy relationship.',tag:'Self-Worth'},
    ]
  }
};

let currentCat = 'earn';
let allItems = [];

function openIdeas(cat){
  currentCat = cat;
  const d = IDEAS[cat];
  document.getElementById('modalEmoji').textContent = d.emoji;
  document.getElementById('modalTitle').textContent = d.title;
  document.getElementById('ideasSearch').value = '';
  allItems = d.items;
  renderIdeas(allItems, d);
  document.getElementById('ideasModal').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeIdeas(){
  document.getElementById('ideasModal').classList.remove('open');
  document.body.style.overflow = '';
}

function renderIdeas(items, d){
  const data = d || IDEAS[currentCat];
  const list = document.getElementById('ideasList');
  list.innerHTML = items.map((item, i) => `
    <div class="idea-item">
      <span class="idea-num" style="color:${data.tagText}">${String(i+1).padStart(2,'0')}</span>
      <div class="idea-content">
        <div class="idea-title">${item.t}</div>
        <div class="idea-desc">${item.d}</div>
        <span class="idea-tag" style="background:${data.tagColor};color:${data.tagText}">${item.tag}</span>
      </div>
    </div>
  `).join('');
  document.getElementById('ideasCountNum').textContent = items.length;
}

function filterIdeas(){
  const q = document.getElementById('ideasSearch').value.toLowerCase();
  const filtered = allItems.filter(i => i.t.toLowerCase().includes(q) || i.d.toLowerCase().includes(q) || i.tag.toLowerCase().includes(q));
  renderIdeas(filtered);
}

document.addEventListener('keydown', e => { if(e.key === 'Escape') closeIdeas(); });
</script>
</body>
</html>
