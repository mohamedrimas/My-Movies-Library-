<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-content">
        <div class="footer-left">
          <h3 class="footer-title">Mohamed Rimas</h3>
          <div class="footer-address">
            <p> 31/4/3/1 Kuruduwatta Mosque Ln.
  </p>
            <p>Nawala Rd Colombo, </p>
            <p>Srilanka</p>
          </div>
        </div>
        
        <div class="footer-right">
          <div class="social-section">
            <span class="follow-text">Follow us on</span>
            <div class="social-icons">
              <a href="#" class="social-link" aria-label="Twitter">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                </svg>
              </a>
              <a href="#" class="social-link" aria-label="YouTube">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
      
      <div class="footer-bottom">
        <div class="copyright">
          <p>Copyright © 2025  All rights reserved.</p>
        </div>
        <div class="credits">
          <p>
            Photos by 
            <a href="#" class="credit-link">Felix Mooneeram</a> & 
            <a href="#" class="credit-link">Serge Kutuzov</a> on 
            <a href="#" class="credit-link">Unsplash</a>
          </p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background-color: #2a2a2a;
  color: #ffffff;
  padding: 40px 0 20px 0;
  margin-top: auto;
}

.footer-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 10%;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 40px;
  padding-bottom: 30px;
  border-bottom: 1px solid #444;
}

.footer-left {
  flex: 1;
}

.footer-title {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 20px;
  color: #ffffff;
}

.footer-address {
  color: #cccccc;
}

.footer-address p {
  margin: 5px 0;
  font-size: 0.9rem;
  line-height: 1.4;
}

.footer-right {
  display: flex;
  align-items: center;
}

.social-section {
  display: flex;
  align-items: center;
  gap: 15px;
}

.follow-text {
  color: #cccccc;
  font-size: 0.9rem;
}

.social-icons {
  display: flex;
  gap: 10px;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 35px;
  height: 35px;
  background-color: #444;
  border-radius: 4px;
  color: #ffffff;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.social-link:hover {
  background-color: #f39c12;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.8rem;
  color: #888;
}

.copyright p,
.credits p {
  margin: 0;
}

.credit-link {
  color: #888;
  text-decoration: underline;
  transition: color 0.3s ease;
}

.credit-link:hover {
  color: #f39c12;
}

@media (max-width: 1024px) {
  .footer-container {
    padding: 0 8%;
  }
  
  .footer-content {
    gap: 25px;
  }
  
  .social-section {
    gap: 12px;
  }
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    gap: 30px;
    text-align: center;
    align-items: center;
  }
  
  .footer-left {
    text-align: center;
  }
  
  .footer-bottom {
    flex-direction: column;
    gap: 15px;
    text-align: center;
  }
  
  .footer-container {
    padding: 0 5%;
  }
  
  .social-section {
    justify-content: center;
  }
  
  .footer-title {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .footer {
    padding: 30px 0 15px 0;
  }
  
  .footer-content {
    margin-bottom: 30px;
    padding-bottom: 20px;
  }
  
  .social-section {
    flex-direction: column;
    gap: 10px;
  }
  
  .social-icons {
    justify-content: center;
  }
  
  .footer-title {
    font-size: 1rem;
    margin-bottom: 15px;
  }
  
  .footer-address p {
    font-size: 0.85rem;
  }
  
  .follow-text {
    font-size: 0.85rem;
  }
  
  .social-link {
    width: 32px;
    height: 32px;
  }
  
  .footer-bottom {
    font-size: 0.75rem;
    gap: 10px;
  }
  
  .footer-container {
    padding: 0 4%;
  }
}
</style>
