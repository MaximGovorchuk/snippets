public interface BaseRepository {
    void refresh(User user);
}

public class BaseRepositoryImpl extends SimpleJpaRepository<User, Long> implements BaseRepository {
    private final EntityManager entityManager;

    public BaseRepositoryImpl(JpaMetamodelEntityInformation<User, Long> jpaMetamodelEntityInformation,
                              EntityManager entityManager) {
        super(jpaMetamodelEntityInformation, entityManager);
        this.entityManager = entityManager;
    }

    @Override
    public void refresh(User user) {
        entityManager.refresh(user);
    }
}


public interface UserRepository extends CrudRepository<User, Long>, BaseRepository {
}

