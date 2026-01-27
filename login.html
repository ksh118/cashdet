import { useState, useEffect } from 'react';
import { useRouter } from 'next/router';
import { createClient } from '@supabase/supabase-js';

// Supabase 클라이언트 초기화
const supabase = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL,
  process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY
);

export default function AuthPage() {
  const router = useRouter();
  const [isSignUp, setIsSignUp] = useState(false); // 로그인/회원가입 모드 전환
  
  // 입력 상태 관리
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [nickname, setNickname] = useState('');

  // 1. 세션 체크: 이미 로그인된 경우 홈으로 리다이렉트
  useEffect(() => {
    const checkUser = async () => {
      const { data: { session } } = await supabase.auth.getSession();
      if (session) router.push('/home');
    };
    checkUser();
  }, [router]);

  // 2. 유효성 검사 (Regex)
  const validateForm = () => {
    const nicknameRegex = /^[가-힣a-zA-Z0-9]{2,10}$/; // 한글/영문/숫자 2~10자 (공백X)
    const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,16}$/; // 대소문자/숫자/특수문자 필수 8~16자

    if (isSignUp && !nicknameRegex.test(nickname)) {
      alert("닉네임은 한글, 영문, 숫자만 가능하며 2~10자여야 합니다.");
      return false;
    }
    if (!passwordRegex.test(password)) {
      alert("비밀번호는 영문 대/소문자, 숫자, 특수문자를 포함해 8~16자여야 합니다.");
      return false;
    }
    return true;
  };

  // 3. 회원가입/로그인 처리
  const handleSubmit = async (e) => {
    e.preventDefault();
    if (!validateForm()) return;

    if (isSignUp) {
      // 회원가입
      const { data, error } = await supabase.auth.signUp({
        email,
        password,
        options: { data: { display_name: nickname } }
      });
      if (error) alert("회원가입 에러: " + error.message);
      else {
        alert("회원가입 성공! 이메일 인증을 확인하거나 로그인해 주세요.");
        setIsSignUp(false);
      }
    } else {
      // 로그인
      const { data, error } = await supabase.auth.signInWithPassword({ email, password });
      if (error) alert("로그인 실패: 이메일 또는 비밀번호를 확인하세요.");
      else router.push('/home');
    }
  };

  // 4. 구글 로그인
  const handleGoogleLogin = async () => {
    await supabase.auth.signInWithOAuth({
      provider: 'google',
      options: { redirectTo: window.location.origin + '/home' }
    });
  };

  return (
    <div className="auth-wrapper">
      <div className="auth-box">
        <h1 className="title">캐시뎃 {isSignUp ? 'Sign Up' : 'Log In'}</h1>
        
        <form onSubmit={handleSubmit} className="auth-form">
          <div className="input-group">
            <img src="/email-icon.png" alt="" className="icon" />
            <input 
              type="email" 
              placeholder="이메일" 
              value={email} 
              onChange={(e) => setEmail(e.target.value)} 
              required 
            />
          </div>

          {isSignUp && (
            <div className="input-group">
              <input 
                type="text" 
                placeholder="닉네임 (2~10자)" 
                value={nickname} 
                onChange={(e) => setNickname(e.target.value)} 
                required 
              />
            </div>
          )}

          <div className="input-group">
            <img src="/lock-icon.png" alt="" className="icon" />
            <input 
              type="password" 
              placeholder="비밀번호" 
              value={password} 
              onChange={(e) => setPassword(e.target.value)} 
              required 
            />
          </div>

          <button type="submit" className="main-btn">
            {isSignUp ? '회원가입' : 'Log In'}
          </button>
        </form>

        <div className="toggle-text">
          <span onClick={() => setIsSignUp(!isSignUp)}>
            {isSignUp ? '이미 계정이 있으신가요? 로그인' : '계정이 없으신가요? 회원가입'}
          </span>
        </div>

        <div className="divider"><span>or</span></div>

        <button onClick={handleGoogleLogin} className="google-btn">
          <img src="/google-logo.png" alt="" width="20" /> Google
        </button>
      </div>

      <style jsx>{`
        .auth-wrapper { display: flex; justify-content: center; align-items: center; min-height: 100vh; background: #fff; }
        .auth-box { width: 100%; max-width: 380px; padding: 40px 20px; text-align: center; }
        .title { font-size: 28px; font-weight: bold; margin-bottom: 30px; }
        .input-group { position: relative; margin-bottom: 15px; }
        input { width: 100%; padding: 15px; border: 1px solid #e1e1e1; border-radius: 8px; font-size: 16px; outline: none; }
        input:focus { border-color: #007bff; }
        .main-btn { width: 100%; padding: 15px; background: #007bff; color: white; border: none; border-radius: 8px; font-size: 18px; font-weight: bold; cursor: pointer; margin-top: 10px; }
        .toggle-text { margin-top: 20px; font-size: 14px; color: #007bff; cursor: pointer; }
        .divider { margin: 25px 0; border-bottom: 1px solid #eee; position: relative; }
        .divider span { position: absolute; top: -10px; left: 50%; transform: translateX(-50%); background: white; padding: 0 10px; color: #999; }
        .google-btn { width: 100%; padding: 12px; background: white; border: 1px solid #ddd; border-radius: 8px; display: flex; align-items: center; justify-content: center; gap: 10px; font-size: 16px; cursor: pointer; }
      `}</style>
    </div>
  );
}
