# ExtendedXP-Core-Api-implementation
Soarce code for function implementation of Extended XP Project 
Extended XP is a project aimed at patching windows XP native files to add missing api .
Implementation of following function are done so far 
if you use this codes as wrapper kindly declare it as dll export 
Kernel32::
GetTickCount64
unsigned __int64 GetTickCount64()
{
  _DWORD *v0; // edi@1

  HIWORD(v0) = 32766;
  while ( 1 )
  {
    if ( !v7FFE0308 )
      return GetTickCount();
    if ( v7FFE0304 == v7FFE0308 )
      break;
    _mm_pause();
  }
  LOWORD(v0) = 4;
  return (v7FFE0304 * (unsigned __int64)*v0 << 8) + (v7FFE0300 * (unsigned __int64)*v0 >> 24);
}
AcquireSRWLockExclusive
AcquireSRWLockShared
InitializeSRWLock
ReleaseSRWLockExclusive
ReleaseSRWLockShared
TryAcquireSRWLockExclusive
TryAcquireSRWLockShared 
{
  return 1;
}
QueryThreadCycleTime 
signed int __stdcall QueryThreadCycleTime(int a1, _QWORD *a2)
{
  signed int result; // eax@2

  if ( a2 )
  {
    *a2 = 3000i64 * GetTickCount();
    result = 1;
  }
  else
  {
    result = 0;
  }
  return result;
}
SetThreadStackGuarantee 
{
  return 1;
}
InitializeCriticalSectionEx 
BOOL __stdcall InitializeCriticalSectionEx(LPCRITICAL_SECTION lpCriticalSection, DWORD dwSpinCount, int a3)
{
  return InitializeCriticalSectionAndSpinCount(lpCriticalSection, dwSpinCount);
}
FlsAlloc
DWORD __stdcall FlsAlloc(int a1)
{
  return TlsAlloc();
}
FlsFree
BOOL __stdcall FlsFree(DWORD dwTlsIndex)
{
  return TlsFree(dwTlsIndex);
}
FlsGetValue
LPVOID __stdcall FlsGetValue(DWORD dwTlsIndex)
{
  return TlsGetValue(dwTlsIndex);
}
FlsSetValue 
BOOL __stdcall FlsSetValue(DWORD dwTlsIndex, LPVOID lpTlsValue)
{
  return TlsSetValue(dwTlsIndex, lpTlsValue);
}
