<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>WorldFg – Global Social Feedback Platform</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>

<!-- AUTH MODAL: Login / Signup + Email Verification -->
<div id="authModal" class="auth-overlay">
  <div class="auth-card">
    <div class="auth-header"><h2><i class="fab fa-facebook-🌎"></i> WorldFg</h2><p>Connect, share feedback & grow together</p></div>
    <div id="loginForm">
      <div class="input-group"><input type="email" id="loginEmail" placeholder="Email address"></div>
      <div class="input-group"><input type="password" id="loginPassword" placeholder="Password"></div>
      <button class="btn-auth" id="doLoginBtn">Log In</button>
      <div class="switch-mode">No account? <span id="showSignupBtn">Create new account</span></div>
      <div id="loginError" style="color:#e41e3f; font-size:0.7rem; text-align:center; margin-top:10px;"></div>
    </div>
    <div id="signupForm" style="display:none;">
      <div class="input-group"><input type="text" id="signupName" placeholder="Full name"></div>
      <div class="input-group"><input type="email" id="signupEmail" placeholder="Email address"></div>
      <div class="input-group"><input type="password" id="signupPassword" placeholder="New password"></div>
      <button class="btn-auth" id="doSignupBtn">Sign Up</button>
      <div class="switch-mode">Already have an account? <span id="showLoginBtn">Log In</span></div>
      <div id="signupError" style="color:#e41e3f; font-size:0.7rem;"></div>
    </div>
    <div id="verifyBox" class="verify-box">
      <p style="font-weight:600;">Verification required</p>
      <p style="font-size:0.8rem;">Enter 6-digit code sent to your email</p>
      <input type="text" id="verifyCodeInput" style="width:100%; padding:12px; border-radius:40px; margin:10px 0; border:1px solid #ccc;">
      <button class="btn-auth" id="verifySubmitBtn">Verify Account</button>
    </div>
  </div>
</div>

<!-- MAIN WorldFg APP -->
<div id="appContainer" class="app-container">
  <div class="top-nav">
    <div class="logo"><i class="fab fa-facebook-f"></i> WorldFg</div>
    <div class="search-area"><i class="fas fa-search"></i><input type="text" id="globalSearchInput" placeholder="Search friends, posts, videos..."></div>
    <div class="nav-icons">
      <div class="nav-icon" id="friendRequestIcon"><i class="fas fa-user-friends"></i><span id="requestBadge" class="badge" style="display:none;">0</span></div>
      <div class="nav-icon" id="logoutNavBtn"><i class="fas fa-sign-out-alt"></i></div>
    </div>
  </div>

  <div class="main-grid">
    <!-- LEFT SIDEBAR: profile + menu -->
    <div class="left-sidebar">
      <div class="profile-card" id="profileCard">
        <div class="cover-area"><img id="coverImageDisplay" class="cover-img" src="https://picsum.photos/300/100?random=1"></div>
        <img id="profileImageDisplay" class="profile-avatar" src="https://randomuser.me/api/portraits/men/1.jpg">
        <h4 id="profileNameDisplay">User Name</h4>
        <button class="edit-profile-btn" id="openProfileEditor"><i class="fas fa-edit"></i> Edit Profile</button>
      </div>
      <div class="menu-list">
        <div class="menu-item" data-page="feed"><i class="fas fa-newspaper"></i> News Feed</div>
        <div class="menu-item" data-page="friends"><i class="fas fa-users"></i> Friends</div>
        <div class="menu-item" data-page="videos"><i class="fas fa-video"></i> Videos</div>
        <div class="menu-item" data-page="feedback"><i class="fas fa-comment-dots"></i> Feedback Hub</div>
      </div>
    </div>

    <!-- CENTER FEED -->
    <div class="feed-column" id="dynamicFeedColumn">
      <div class="create-post">
        <div class="post-top"><img id="feedUserAvatar" src=""><input type="text" id="postTextInput" placeholder="What's on your mind? Share your feedback..."></div>
        <div class="post-actions">
          <span class="post-action" id="photoVideoTrigger"><i class="fas fa-image"></i> Photo/Video</span>
          <span class="post-action" id="submitPostBtn"><i class="fas fa-paper-plane"></i> Post</span>
        </div>
        <input type="file" id="postMediaFile" accept="image/*,video/*" style="display:none">
      </div>
      <div id="newsFeedContainer"></div>
    </div>

    <!-- RIGHT PANEL -->
    <div class="right-panel">
      <div class="section-card">
        <h4><i class="fas fa-user-plus"></i> Friend Requests</h4>
        <div id="requestsList">Loading...</div>
      </div>
      <div class="section-card">
        <h4><i class="fas fa-users"></i> People You May Know</h4>
        <div id="suggestionsList"></div>
      </div>
    </div>
  </div>
</div>

<!-- Profile Editor Modal -->
<div id="profileModal" class="modal">
  <div class="modal-content">
    <h3>Edit Profile</h3>
    <label>Profile Picture</label>
    <input type="file" id="profilePicUpload" accept="image/*" class="file-input">
    <label>Cover Photo</label>
    <input type="file" id="coverUpload" accept="image/*" class="file-input">
    <button id="saveProfileChanges" class="btn-auth" style="margin-top:15px;">Save Changes</button>
    <button onclick="closeProfileModal()" style="margin-top:10px; width:100%;">Cancel</button>
  </div>
</div>

<!-- Toast notification -->
<div id="toastMsg" class="toast-msg"></div>

<script src="script.js"></script>
</body>
</html>
