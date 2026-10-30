<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Peer Learning Partner</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    .tab-content { display: none; }
    .tab-content.active { display: block; }
  </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans min-h-screen flex flex-col">

  <!-- Header / Navigation -->
  <header class="bg-indigo-600 text-white shadow-md sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap justify-between items-center">
      <div class="flex items-center space-x-3">
        <i class="fa-solid font-bold text-2xl fa-graduation-cap"></i>
        <h1 class="text-xl font-bold tracking-wide">Peer Partner</h1>
      </div>
      
      <!-- Nav Tabs -->
      <nav class="flex space-x-1 sm:space-x-4 mt-2 sm:mt-0 text-sm font-medium">
        <button onclick="switchTab('match')" id="btn-match" class="tab-btn px-3 py-2 rounded-lg bg-indigo-700 hover:bg-indigo-800 transition">
          <i class="fa-solid fa-handshake mr-1.5"></i> Find Mentor
        </button>
        <button onclick="switchTab('groups')" id="btn-groups" class="tab-btn px-3 py-2 hover:bg-indigo-700 rounded-lg transition">
          <i class="fa-solid fa-users mr-1.5"></i> Study Groups
        </button>
        <button onclick="switchTab('tracker')" id="btn-tracker" class="tab-btn px-3 py-2 hover:bg-indigo-700 rounded-lg transition">
          <i class="fa-solid fa-chart-line mr-1.5"></i> Activity Tracker
        </button>
        <button onclick="switchTab('teacher')" id="btn-teacher" class="tab-btn px-3 py-2 hover:bg-indigo-700 rounded-lg transition">
          <i class="fa-solid fa-user-check mr-1.5"></i> Teacher Portal
        </button>
      </nav>
    </div>
  </header>

  <!-- Main Content Container -->
  <main class="max-w-7xl mx-auto px-4 py-8 flex-grow w-full">

    <!-- 1. MENTOR MATCHING SECTION -->
    <section id="tab-match" class="tab-content active space-y-6">
      <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
        <div class="md:flex justify-between items-center">
          <div>
            <h2 class="text-2xl font-bold text-slate-800">Peer Mentor Matcher</h2>
            <p class="text-slate-500 mt-1">Connect with confident peer mentors ready to help in specific subjects.</p>
          </div>
          <!-- Subject Filter -->
          <div class="mt-4 md:mt-0 flex items-center space-x-2">
            <label for="subject-filter" class="font-medium text-slate-600">Subject:</label>
            <select id="subject-filter" onchange="filterMentors()" class="bg-slate-100 border border-slate-300 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
              <option value="All">All Subjects</option>
              <option value="English">English</option>
              <option value="Mathematics">Mathematics</option>
              <option value="Science">Science</option>
              <option value="Computer Science">Computer Science</option>
            </select>
          </div>
        </div>
      </div>

      <!-- Mentor Cards Grid -->
      <div id="mentor-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- Mentor cards populated by JS -->
      </div>
    </section>

    <!-- 2. STUDY GROUPS SECTION -->
    <section id="tab-groups" class="tab-content space-y-6">
      <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
        <h2 class="text-2xl font-bold text-slate-800">Subject-Wise Study Groups</h2>
        <p class="text-slate-500 mt-1">Join structured peer study circles to learn together.</p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <!-- Groups List -->
        <div class="lg:col-span-1 space-y-4" id="group-list">
          <!-- Populated by JS -->
        </div>

        <!-- Active Group Chat Window -->
        <div class="lg:col-span-2 bg-white rounded-xl shadow-sm border border-slate-200 flex flex-col h-[500px]">
          <div class="p-4 border-b border-slate-200 flex justify-between items-center bg-slate-50 rounded-t-xl">
            <div>
              <h3 id="chat-title" class="font-bold text-slate-800">English Literature Discussion</h3>
              <p id="chat-subtitle" class="text-xs text-slate-500">3 Members • Active now</p>
            </div>
            <span class="bg-emerald-100 text-emerald-800 text-xs px-2.5 py-1 rounded-full font-medium">Group Session Live</span>
          </div>

          <!-- Messages Body -->
          <div id="chat-messages" class="flex-grow p-4 space-y-3 overflow-y-auto">
            <div class="bg-slate-100 p-3 rounded-lg max-w-md">
              <p class="text-xs font-bold text-slate-600 mb-1">Alex (Mentor)</p>
              <p class="text-sm">Welcome everyone! Today we're reviewing essay structures for Shakespeare's Hamlet.</p>
            </div>
            <div class="bg-indigo-50 p-3 rounded-lg max-w-md ml-auto">
              <p class="text-xs font-bold text-indigo-700 mb-1">You</p>
              <p class="text-sm">Thanks Alex! I have a question about writing thesis statements.</p>
            </div>
          </div>

          <!-- Message Input -->
          <form onsubmit="sendMessage(event)" class="p-3 border-t border-slate-200 flex space-x-2">
            <input id="chat-input" type="text" placeholder="Type your question or response..." class="flex-grow border border-slate-300 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
            <button type="submit" class="bg-indigo-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-indigo-700 transition">
              <i class="fa-solid fa-paper-plane"></i>
            </button>
          </form>
        </div>
      </div>
    </section>

    <!-- 3. ACTIVITY TRACKER SECTION -->
    <section id="tab-tracker" class="tab-content space-y-6">
      <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
        <h2 class="text-2xl font-bold text-slate-800">Group Learning Activity Tracker</h2>
        <p class="text-slate-500 mt-1">Track hours, study streaks, and progress made with peer mentors.</p>
      </div>

      <!-- Overview Stats -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
        <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm flex items-center space-x-4">
          <div class="bg-indigo-100 text-indigo-600 p-3 rounded-lg"><i class="fa-solid fa-clock text-xl"></i></div>
          <div>
            <p class="text-xs text-slate-500">Total Hours</p>
            <p class="text-2xl font-bold">14.5 hrs</p>
          </div>
        </div>
        <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm flex items-center space-x-4">
          <div class="bg-emerald-100 text-emerald-600 p-3 rounded-lg"><i class="fa-solid fa-fire text-xl"></i></div>
          <div>
            <p class="text-xs text-slate-500">Study Streak</p>
            <p class="text-2xl font-bold">5 Days</p>
          </div>
        </div>
        <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm flex items-center space-x-4">
          <div class="bg-amber-100 text-amber-600 p-3 rounded-lg"><i class="fa-solid fa-book-open text-xl"></i></div>
          <div>
            <p class="text-xs text-slate-500">Completed Sessions</p>
            <p class="text-2xl font-bold">12 Sessions</p>
          </div>
        </div>
        <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm flex items-center space-x-4">
          <div class="bg-purple-100 text-purple-600 p-3 rounded-lg"><i class="fa-solid fa-award text-xl"></i></div>
          <div>
            <p class="text-xs text-slate-500">Badges Earned</p>
            <p class="text-2xl font-bold">4 Badges</p>
          </div>
        </div>
      </div>

      <!-- Activity Table -->
      <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
        <div class="p-4 border-b border-slate-200 bg-slate-50">
          <h3 class="font-bold text-slate-800">Recent Peer Learning Log</h3>
        </div>
        <div class="overflow-x-auto">
          <table class="w-full text-left border-collapse text-sm">
            <thead>
              <tr class="bg-slate-100 border-b border-slate-200 text-slate-600">
                <th class="p-3 font-semibold">Date</th>
                <th class="p-3 font-semibold">Subject</th>
                <th class="p-3 font-semibold">Mentor/Group</th>
                <th class="p-3 font-semibold">Duration</th>
                <th class="p-3 font-semibold">Status</th>
              </tr>
            </thead>
            <tbody id="activity-log-body">
              <tr class="border-b border-slate-100 hover:bg-slate-50">
                <td class="p-3">Oct 28, 2026</td>
                <td class="p-3"><span class="bg-blue-100 text-blue-800 text-xs px-2 py-0.5 rounded">English</span></td>
                <td class="p-3">Alex Vance (Mentor)</td>
                <td class="p-3">1 hr 30 mins</td>
                <td class="p-3"><span class="text-emerald-600 font-medium"><i class="fa-solid fa-circle-check mr-1"></i>Verified</span></td>
              </tr>
              <tr class="border-b border-slate-100 hover:bg-slate-50">
                <td class="p-3">Oct 26, 2026</td>
                <td class="p-3"><span class="bg-amber-100 text-amber-800 text-xs px-2 py-0.5 rounded">Math</span></td>
                <td class="p-3">Calculus Pioneers Group</td>
                <td class="p-3">2 hrs 00 mins</td>
                <td class="p-3"><span class="text-emerald-600 font-medium"><i class="fa-solid fa-circle-check mr-1"></i>Verified</span></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- 4. TEACHER SUPERVISION SECTION -->
    <section id="tab-teacher" class="tab-content space-y-6">
      <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
        <div class="flex justify-between items-center">
          <div>
            <h2 class="text-2xl font-bold text-slate-800">Teacher Supervision Dashboard</h2>
            <p class="text-slate-500 mt-1">Supervise mentorship pairs, approve new requests, and provide guidance.</p>
          </div>
          <span class="bg-indigo-100 text-indigo-700 text-xs px-3 py-1 rounded-full font-bold">Faculty View</span>
        </div>
      </div>

      <!-- Pending Mentorship Approvals -->
      <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 space-y-4">
        <h3 class="text-lg font-bold text-slate-800">Pending Mentorship Requests</h3>
        <div id="pending-requests" class="space-y-3">
          <!-- Populated by JS -->
        </div>
      </div>

      <!-- Active Mentoring Pairs Monitor -->
      <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 space-y-4">
        <h3 class="text-lg font-bold text-slate-800">Active Peer Partnerships</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="active-pairs">
          <!-- Populated by JS -->
        </div>
      </div>
    </section>

  </main>

  <!-- Notification Toast -->
  <div id="toast" class="fixed bottom-5 right-5 bg-slate-800 text-white px-4 py-3 rounded-lg shadow-lg hidden transition-opacity duration-300 flex items-center space-x-2">
    <i class="fa-solid fa-circle-info text-indigo-400"></i>
    <span id="toast-message">Notification message</span>
  </div>

  <!-- JavaScript Logic -->
  <script>
    // Sample Data
    const mentors = [
      { id: 1, name: "Alex Vance", subject: "English", grade: "Grade 11", strength: "Essay Writing & Grammar", bio: "Passionate about literature and confident in helping peers structure analytical essays.", rating: "4.9" },
      { id: 2, name: "Sarah Chen", subject: "Mathematics", grade: "Grade 12", strength: "Calculus & Algebra", bio: "Loves breaking down complex math problems into simple step-by-step solutions.", rating: "5.0" },
      { id: 3, name: "David Kim", subject: "Science", grade: "Grade 11", strength: "Physics & Chemistry", bio: "Available for lab report assistance and conceptual physics study.", rating: "4.8" },
      { id: 4, name: "Maya Patel", subject: "Computer Science", grade: "Grade 10", strength: "Python & Logic", bio: "Helps beginners learn basic programming concepts and debug code.", rating: "4.9" }
    ];

    const studyGroups = [
      { id: 1, name: "English Literature Hub", subject: "English", members: 5, description: "Weekly discussions on set literature books and essay feedback." },
      { id: 2, name: "Calculus Pioneers", subject: "Mathematics", members: 8, description: "Solving daily calculus problem sets together." },
      { id: 3, name: "Physics Problem Solvers", subject: "Science", members: 4, description: "Preparing for exams through physics conceptual questions." }
    ];

    let pendingRequests = [
      { id: 101, mentor: "Alex Vance", mentee: "John Doe", subject: "English", date: "Today" },
      { id: 102, mentor: "Sarah Chen", mentee: "Emma Watson", subject: "Mathematics", date: "Yesterday" }
    ];

    const activePairs = [
      { mentor: "David Kim", mentee: "Lucas Hood", subject: "Science", sessions: 4, lastActive: "2 days ago" },
      { mentor: "Maya Patel", mentee: "Sofia Blake", subject: "Computer Science", sessions: 6, lastActive: "Yesterday" }
    ];

    // Navigation Switch
    function switchTab(tabName) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.tab-btn').forEach(el => el.classList.replace('bg-indigo-700', 'hover:bg-indigo-700'));

      document.getElementById(`tab-${tabName}`).classList.add('active');
      const activeBtn = document.getElementById(`btn-${tabName}`);
      activeBtn.classList.add('bg-indigo-700');
    }

    // Render Mentors
    function renderMentors(filter = "All") {
      const grid = document.getElementById('mentor-grid');
      grid.innerHTML = '';

      const filtered = filter === "All" ? mentors : mentors.filter(m => m.subject === filter);

      if (filtered.length === 0) {
        grid.innerHTML = `<p class="col-span-full text-slate-500 py-8 text-center">No mentors found for this subject.</p>`;
        return;
      }

      filtered.forEach(m => {
        grid.innerHTML += `
          <div class="bg-white rounded-xl p-5 shadow-sm border border-slate-200 flex flex-col justify-between">
            <div>
              <div class="flex justify-between items-start mb-3">
                <div>
                  <h3 class="font-bold text-slate-800 text-lg">${m.name}</h3>
                  <p class="text-xs text-slate-500">${m.grade}</p>
                </div>
                <span class="bg-indigo-50 text-indigo-700 font-semibold text-xs px-2.5 py-1 rounded-full">${m.subject}</span>
              </div>
              <p class="text-xs font-semibold text-indigo-600 mb-2"><i class="fa-solid fa-star mr-1"></i>${m.strength}</p>
              <p class="text-slate-600 text-sm mb-4">${m.bio}</p>
            </div>
            <button onclick="requestMentorship('${m.name}', '${m.subject}')" class="w-full bg-indigo-600 text-white py-2 rounded-lg text-sm font-medium hover:bg-indigo-700 transition flex items-center justify-center space-x-2">
              <i class="fa-solid fa-user-plus"></i>
              <span>Request Peer Partnership</span>
            </button>
          </div>
        `;
      });
    }

    function filterMentors() {
      const selected = document.getElementById('subject-filter').value;
      renderMentors(selected);
    }

    // Render Study Groups
    function renderGroups() {
      const list = document.getElementById('group-list');
      list.innerHTML = '';

      studyGroups.forEach(g => {
        list.innerHTML += `
          <div class="bg-white p-4 rounded-xl shadow-sm border border-slate-200 space-y-2 hover:border-indigo-300 transition">
            <div class="flex justify-between items-center">
              <h4 class="font-bold text-slate-800">${g.name}</h4>
              <span class="text-xs bg-slate-100 text-slate-600 px-2 py-0.5 rounded">${g.members} Members</span>
            </div>
            <p class="text-xs text-slate-500">${g.description}</p>
            <button onclick="showToast('Joined group: ${g.name}')" class="w-full text-xs font-semibold text-indigo-600 hover:text-indigo-800 bg-indigo-50 py-1.5 rounded-lg transition">
              Join Group
            </button>
          </div>
        `;
      });
    }

    // Render Teacher Supervision Dashboard
    function renderTeacherDashboard() {
      const reqContainer = document.getElementById('pending-requests');
      reqContainer.innerHTML = '';

      if (pendingRequests.length === 0) {
        reqContainer.innerHTML = `<p class="text-sm text-slate-500">No pending requests requiring approval.</p>`;
      } else {
        pendingRequests.forEach(r => {
          reqContainer.innerHTML += `
            <div class="flex flex-wrap justify-between items-center p-3 bg-slate-50 rounded-lg border border-slate-200">
              <div class="text-sm">
                <span class="font-bold text-slate-800">${r.mentee}</span> requested mentorship from 
                <span class="font-bold text-slate-800">${r.mentor}</span> in 
                <span class="text-indigo-600 font-semibold">${r.subject}</span>.
              </div>
              <div class="flex space-x-2 mt-2 sm:mt-0">
                <button onclick="approveRequest(${r.id})" class="bg-emerald-600 text-white text-xs px-3 py-1.5 rounded-lg hover:bg-emerald-700 transition">
                  Approve
                </button>
                <button onclick="rejectRequest(${r.id})" class="bg-rose-100 text-rose-700 text-xs px-3 py-1.5 rounded-lg hover:bg-rose-200 transition">
                  Decline
                </button>
              </div>
            </div>
          `;
        });
      }

      const pairsContainer = document.getElementById('active-pairs');
      pairsContainer.innerHTML = '';
      activePairs.forEach(p => {
        pairsContainer.innerHTML += `
          <div class="p-4 border border-slate-200 rounded-lg bg-slate-50 space-y-2">
            <div class="flex justify-between items-center">
              <span class="text-xs font-bold text-indigo-600">${p.subject}</span>
              <span class="text-xs text-slate-400">Active: ${p.lastActive}</span>
            </div>
            <p class="text-sm font-semibold text-slate-800">${p.mentor} <span class="text-slate-400 font-normal">mentoring</span> ${p.mentee}</p>
            <p class="text-xs text-slate-500">${p.sessions} sessions completed</p>
          </div>
        `;
      });
    }

    // Interactive Actions
    function requestMentorship(mentorName, subject) {
      pendingRequests.push({
        id: Date.now(),
        mentor: mentorName,
        mentee: "You",
        subject: subject,
        date: "Just now"
      });
      renderTeacherDashboard();
      showToast(`Request sent to ${mentorName}! Awaiting teacher supervision approval.`);
    }

    function approveRequest(id) {
      const req = pendingRequests.find(r => r.id === id);
      if (req) {
        activePairs.push({
          mentor: req.mentor,
          mentee: req.mentee,
          subject: req.subject,
          sessions: 0,
          lastActive: "Just now"
        });
        pendingRequests = pendingRequests.filter(r => r.id !== id);
        renderTeacherDashboard();
        showToast("Mentorship request approved!");
      }
    }

    function rejectRequest(id) {
      pendingRequests = pendingRequests.filter(r => r.id !== id);
      renderTeacherDashboard();
      showToast("Request declined.");
    }

    function sendMessage(e) {
      e.preventDefault();
      const input = document.getElementById('chat-input');
      const text = input.value.trim();
      if (!text) return;

      const chatBox = document.getElementById('chat-messages');
      chatBox.innerHTML += `
        <div class="bg-indigo-50 p-3 rounded-lg max-w-md ml-auto">
          <p class="text-xs font-bold text-indigo-700 mb-1">You</p>
          <p class="text-sm">${text}</p>
        </div>
      `;
      input.value = '';
      chatBox.scrollTop = chatBox.scrollHeight;
    }

    function showToast(message) {
      const toast = document.getElementById('toast');
      document.getElementById('toast-message').innerText = message;
      toast.classList.remove('hidden');
      setTimeout(() => {
        toast.classList.add('hidden');
      }, 3500);
    }

    // Initialize Page
    document.addEventListener('DOMContentLoaded', () => {
      renderMentors();
      renderGroups();
      renderTeacherDashboard();
    });
  </script>
</body>
</html>
