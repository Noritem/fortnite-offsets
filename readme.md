# W2S-Offsets-fortnite

#define OFFSET_UWORLD 0xe9ea3f8 //

namespace OFFSETS
{
	uintptr_t Gameinstance = 0x1B8; //
	uintptr_t LocalPlayers = 0x38;
	uintptr_t PlayerController = 0x30;
	uintptr_t LocalPawn = 0x330; //
	uintptr_t PlayerState = 0x2a8; //
	uintptr_t RootComponet = 0x190; //
	uintptr_t PersistentLevel = 0x30;
	uintptr_t ActorCount = 0xA0;
	uintptr_t AActor = 0x98;
	uintptr_t CurrentActor = 0x8;
	uintptr_t Mesh = 0x310;
	uintptr_t Revivefromdbnotime = 0x4388; //
	uintptr_t TeamId = 0x10E8;
	uintptr_t LocalActorPos = 0x128;
	uintptr_t ComponetToWorld = 0x240;
	uintptr_t BoneArray = 0x5a0;
	uintptr_t Velocity = 0x170;
	uintptr_t PawnPrivate = 0x300;
	uintptr_t PlayerArray = 0x2a0;

	uintptr_t ReviveFromDBNOTime = 0x4170;

}

struct Camera
{
	Vector3 Location;
	Vector3 Rotation;
	float FieldOfView;
}; Camera vCamera;

// ScriptStruct Engine.TViewTarget
// Size: 0x790 (Inherited: 0x00)
struct FTViewTarget {
	struct FMinimalViewInfo POV; // 0x10(0x770)
};

struct FFortGameplayAttributeData {
	float Minimum; // 0x10(0x04)
	float Maximum; // 0x14(0x04)
	bool bIsCurrentClamped; // 0x18(0x01)
	bool bIsBaseClamped; // 0x19(0x01)
	bool bShouldClampBase; // 0x1a(0x01)
	char pad_1B[0x1]; // 0x1b(0x01)
	float UnclampedBaseValue; // 0x1c(0x04)
	float UnclampedCurrentValue; // 0x20(0x04)
	char pad_24[0x4]; // 0x24(0x04)
};

// Class FortniteGame.AthenaBigBaseWall
// Size: 0xa58 (Inherited: 0x9c8)
struct AAthenaBigBaseWall{
	float WallGravity; // 0x9c8(0x04)
	float TimeUntilWallComesDown; // 0x9cc(0x04)
	bool bResetBool; // 0x9d0(0x01)
	//enum class EBarrierState BarrierState; // 0x9d1(0x01)
	char pad_9D2[0x6]; // 0x9d2(0x06)
	//struct FScalableFloat ZKillLevel; // 0x9d8(0x28)
	char pad_A00[0x58]; // 0xa00(0x58)

	void WallStartingToComeDown(bool bIsOnBurgerSide); // Function FortniteGame.AthenaBigBaseWall.WallStartingToComeDown // (Event|Protected|BlueprintEvent) // @ game+0x1036c24
	void UpdateWallTime(float, float, float, float); // Function FortniteGame.AthenaBigBaseWall.UpdateWallTime // (Event|Protected|BlueprintEvent) // @ game+0x1036c24
	void ShowOrHideTimer(bool bNewVisibleState); // Function FortniteGame.AthenaBigBaseWall.ShowOrHideTimer // (Event|Protected|BlueprintEvent) // @ game+0x1036c24
	void OnRep_WallGravity(); // Function FortniteGame.AthenaBigBaseWall.OnRep_WallGravity // (Final|Native|Protected) // @ game+0x78b3450
	void OnRep_TimeUntilWallComesDown(); // Function FortniteGame.AthenaBigBaseWall.OnRep_TimeUntilWallComesDown // (Final|Native|Protected) // @ game+0x78b32cc
	void OnRep_ResetBool(); // Function FortniteGame.AthenaBigBaseWall.OnRep_ResetBool // (Final|Native|Protected) // @ game+0x24b6bc4
	void OnRep_BarrierState(); // Function FortniteGame.AthenaBigBaseWall.OnRep_BarrierState // (Final|Native|Protected) // @ game+0x78b2e88
	void OnNewBarrierState(enum class EBarrierState NewState); // Function FortniteGame.AthenaBigBaseWall.OnNewBarrierState // (Event|Protected|BlueprintEvent) // @ game+0x1036c24
};

////////////


D3DXMATRIX Matrix(Vector3 rot, Vector3 origin = Vector3(0, 0, 0))
{
	float radPitch = (rot.x * float(M_PI) / 180.f);
	float radYaw = (rot.y * float(M_PI) / 180.f);
	float radRoll = (rot.z * float(M_PI) / 180.f);

	float SP = sinf(radPitch);
	float CP = cosf(radPitch);
	float SY = sinf(radYaw);
	float CY = cosf(radYaw);
	float SR = sinf(radRoll);
	float CR = cosf(radRoll);

	D3DMATRIX matrix;
	matrix.m[0][0] = CP * CY;
	matrix.m[0][1] = CP * SY;
	matrix.m[0][2] = SP;
	matrix.m[0][3] = 0.f;

	matrix.m[1][0] = SR * SP * CY - CR * SY;
	matrix.m[1][1] = SR * SP * SY + CR * CY;
	matrix.m[1][2] = -SR * CP;
	matrix.m[1][3] = 0.f;

	matrix.m[2][0] = -(CR * SP * CY + SR * SY);
	matrix.m[2][1] = CY * SR - CR * SP * SY;
	matrix.m[2][2] = CR * CP;
	matrix.m[2][3] = 0.f;

	matrix.m[3][0] = origin.x;
	matrix.m[3][1] = origin.y;
	matrix.m[3][2] = origin.z;
	matrix.m[3][3] = 1.f;

	return matrix;
}

D3DMATRIX matrixx(D3DMATRIX pM1, D3DMATRIX pM2)
{
	D3DMATRIX pOut;
	pOut._11 = pM1._11 * pM2._11 + pM1._12 * pM2._21 + pM1._13 * pM2._31 + pM1._14 * pM2._41;
	pOut._12 = pM1._11 * pM2._12 + pM1._12 * pM2._22 + pM1._13 * pM2._32 + pM1._14 * pM2._42;
	pOut._13 = pM1._11 * pM2._13 + pM1._12 * pM2._23 + pM1._13 * pM2._33 + pM1._14 * pM2._43;
	pOut._14 = pM1._11 * pM2._14 + pM1._12 * pM2._24 + pM1._13 * pM2._34 + pM1._14 * pM2._44;
	pOut._21 = pM1._21 * pM2._11 + pM1._22 * pM2._21 + pM1._23 * pM2._31 + pM1._24 * pM2._41;
	pOut._22 = pM1._21 * pM2._12 + pM1._22 * pM2._22 + pM1._23 * pM2._32 + pM1._24 * pM2._42;
	pOut._23 = pM1._21 * pM2._13 + pM1._22 * pM2._23 + pM1._23 * pM2._33 + pM1._24 * pM2._43;
	pOut._24 = pM1._21 * pM2._14 + pM1._22 * pM2._24 + pM1._23 * pM2._34 + pM1._24 * pM2._44;
	pOut._31 = pM1._31 * pM2._11 + pM1._32 * pM2._21 + pM1._33 * pM2._31 + pM1._34 * pM2._41;
	pOut._32 = pM1._31 * pM2._12 + pM1._32 * pM2._22 + pM1._33 * pM2._32 + pM1._34 * pM2._42;
	pOut._33 = pM1._31 * pM2._13 + pM1._32 * pM2._23 + pM1._33 * pM2._33 + pM1._34 * pM2._43;
	pOut._34 = pM1._31 * pM2._14 + pM1._32 * pM2._24 + pM1._33 * pM2._34 + pM1._34 * pM2._44;
	pOut._41 = pM1._41 * pM2._11 + pM1._42 * pM2._21 + pM1._43 * pM2._31 + pM1._44 * pM2._41;
	pOut._42 = pM1._41 * pM2._12 + pM1._42 * pM2._22 + pM1._43 * pM2._32 + pM1._44 * pM2._42;
	pOut._43 = pM1._41 * pM2._13 + pM1._42 * pM2._23 + pM1._43 * pM2._33 + pM1._44 * pM2._43;
	pOut._44 = pM1._41 * pM2._14 + pM1._42 * pM2._24 + pM1._43 * pM2._34 + pM1._44 * pM2._44;

	return pOut;
}


bool IsVec3Valid(Vector3 vec3)
{
	return !(vec3.x == 0 && vec3.y == 0 && vec3.z == 0);
}

bool IsInScreen(Vector3 pos, int over = 30) {
	if (pos.x > -over && pos.x < Width + over && pos.y > -over && pos.y < Height + over) {
		return true;
	}
	else {
		return false;
	}
}

FTransform GetBoneIndex(DWORD_PTR mesh, int index)
{
	DWORD_PTR bonearray;
	bonearray = vmread<DWORD_PTR>(mesh + 0x5B8);

	if (bonearray == NULL)
	{
		bonearray = vmread<DWORD_PTR>(mesh + 0x5C8 + 0x28);
	}
	return vmread<FTransform>(bonearray + (index * 0x60));
}

Vector3 GetBoneWithRotation(DWORD_PTR mesh, int id)
{
	FTransform bone = GetBoneIndex(mesh, id);
	FTransform ComponentToWorld = vmread<FTransform>(mesh + 0x240);

	D3DMATRIX Matrix;
	Matrix = matrixx(bone.ToMatrixWithScale(), ComponentToWorld.ToMatrixWithScale());

	return Vector3(Matrix._41, Matrix._42, Matrix._43);
}

bool isVisible(uint64_t mesh)
{
	float tik = vmread<float>(mesh + 0x330);
	float tok = vmread<float>(mesh + 0x338);
	const float tick = 0.06f;
	return tok + tick >= tik;

}
  
  	auto entityListCopy = entityList;
	float closestDistance = FLT_MAX;
	DWORD_PTR closestPawn = NULL;
	Uworld = KmDrv->Rpm<DWORD_PTR>(base_address + OFFSET_UWORLD);
	DWORD_PTR Gameinstance = KmDrv->Rpm<DWORD_PTR>(Uworld + OFFSETS::Gameinstance);
	DWORD_PTR LocalPlayers = KmDrv->Rpm<DWORD_PTR>(Gameinstance + OFFSETS::LocalPlayers);
	Localplayer = KmDrv->Rpm<DWORD_PTR>(LocalPlayers);
	PlayerController = KmDrv->Rpm<DWORD_PTR>(Localplayer + OFFSETS::PlayerController);
	LocalPawn = KmDrv->Rpm<DWORD_PTR>(PlayerController + OFFSETS::LocalPawn);
	uintptr_t pcmc = KmDrv->Rpm<uint64_t>(PlayerController + 0x330);
	PlayerState = KmDrv->Rpm<DWORD_PTR>(LocalPawn + OFFSETS::PlayerState);
	DWORD_PTR PlayerCameraManager = KmDrv->Rpm<DWORD_PTR>(PlayerController + 0x340);
	PlayerCameraManager = KmDrv->Rpm<DWORD_PTR>(LocalPawn + PlayerCameraManager);
	Rootcomp = KmDrv->Rpm<DWORD_PTR>(LocalPawn + OFFSETS::RootComponet);
	Persistentlevel = KmDrv->Rpm<DWORD_PTR>(Uworld + OFFSETS::PersistentLevel);
	uintptr_t Crrneytwep = KmDrv->Rpm<uintptr_t>(LocalPawn + 0x868);
	DWORD ActorCount = KmDrv->Rpm<DWORD>(Persistentlevel + OFFSETS::ActorCount);
	DWORD_PTR AActors = KmDrv->Rpm<DWORD_PTR>(Persistentlevel + OFFSETS::AActor);
	char bisDying = KmDrv->Rpm<char>(Localplayer + 0x6f8);
	char bisBot = KmDrv->Rpm<char>(PlayerState + 0x292);
	auto bIsReloadingWeapon = KmDrv->Rpm<bool>(Crrneytwep + 0x2B9);
	DWORD_PTR GameState = KmDrv->Rpm<DWORD_PTR>(Uworld + 0x158);//gamestate
	DWORD_PTR PlayerArray = KmDrv->Rpm<DWORD_PTR>(GameState + 0x2A0);//playerarray
	uint64_t CurrentVehicle = KmDrv->Rpm<uint64_t>(LocalPawn + 0x2348); //FortPlayerPawn::CurrentVehicle